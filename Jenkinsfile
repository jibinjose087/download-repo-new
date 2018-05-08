def getProjectName() {
    return 'JenkinsPipeline'
}


def getEnvironment() {
    return  'QA\n' +
            'STG\n' +
            'PRD'
}

def getEmailRecipients() {
    return ''
}


def publishHTMLReports(reportName) {
    // Publish HTML reports (HTML Publisher plugin)
    publishHTML([allowMissing         : true,
                 alwaysLinkToLastBuild: true,
                 keepAll              : true,
                 reportDir            : 'target\\view',
                 reportFiles          : 'index.html',
                 reportName           : reportName])
}

/* Declarative pipeline must be enclosed within a pipeline block */
pipeline {
    // agent section specifies where the entire Pipeline will execute in the Jenkins environment
    agent {
        /**
         * node allows for additional options to be specified
         * you can also specify label '' without the node option
         * if you want to execute the pipeline on any available agent use the option 'agent any'
         */
        node {
            label '' // Execute the Pipeline on an agent available in the Jenkins environment with the provided label
        }
    }

    /**
     * parameters directive provides a list of parameters which a user should provide when triggering the Pipeline
     * some of the valid parameter types are booleanParam, choice, file, text, password, run, or string
     */
    parameters {
        choice(choices: "$environment", description: '', name: 'ENVIRONMENT')
        string(defaultValue: "$emailRecipients",
                description: 'List of email recipients',
                name: 'EMAIL_RECIPIENTS')
    }

    /**
     * stages contain one or more stage directives
     */
    stages {
        /**
         * the stage directive should contain a steps section, an optional agent section, or other stage-specific directives
         * all of the real work done by a Pipeline will be wrapped in one or more stage directives
         */
        stage('Prepare') {
            steps {
                // GIT submodule recursive checkout
                checkout scm: [
                        $class: 'GitSCM',
                        branches: scm.branches,
                        doGenerateSubmoduleConfigurations: false,
                        extensions: [[$class: 'SubmoduleOption',
                                      disableSubmodules: false,
                                      parentCredentials: false,
                                      recursiveSubmodules: true,
                                      reference: '',
                                      trackingSubmodules: false]],
                        submoduleCfg: [],
                        userRemoteConfigs: scm.userRemoteConfigs
                ]
                // copy managed files to workspace
                script {
                    if(params.USE_INPUT_DUNS) {
                        configFileProvider([configFile(fileId: '609999e4-446c-4705-a024-061ed7ca2a11',
                                targetLocation: 'input/')]) {
                            echo 'Managed file copied to workspace'
                        }
                    }
                }
            }
        }

        stage('User Input') {
            // when directive allows the Pipeline to determine whether the stage should be executed depending on the given condition
            // built-in conditions - branch, expression, allOf, anyOf, not etc.
            when {
                // Execute the stage when the specified Groovy expression evaluates to true
                expression {
                    return params.ENVIRONMENT ==~ /(?i)(STG|PRD)/
                }
            }
            /**
             * steps section defines a series of one or more steps to be executed in a given stage directive
             */
            steps {
                // script step takes a block of Scripted Pipeline and executes that in the Declarative Pipeline
                script {
                    // This step pauses Pipeline execution and allows the user to interact and control the flow of the build.
                    // Only a basic "process" or "abort" option is provided in the stage view
                    input message: '', ok: 'Proceed',
                            parameters: [
                                    string(name: '', description: ''),
                            ]
                }
            }
        }

        stage('Maven version') {
            steps {
                echo "Hello, Maven"
                sh "mvn --version" // Runs a Bourne shell script, typically on a Unix node
            }
        }


    }

    /**
     * post section defines actions which will be run at the end of the Pipeline run or stage
     * post section condition blocks: always, changed, failure, success, unstable, and aborted
     */
    post {
        // Run regardless of the completion status of the Pipeline run
        always {
            // send email
            // email template to be loaded from managed files
            emailext body: '${SCRIPT,template="managed:EmailTemplate"}',
                    attachLog: true,
                    compressLog: true,
                    attachmentsPattern: "$reportZipFile",
                    mimeType: 'text/html',
                    subject: "Pipeline Build ${BUILD_NUMBER}",
                    to: "${params.EMAIL_RECIPIENTS}"

            // clean up workspace
            deleteDir()
        }
        // Only run the steps if the current Pipeline’s or stage’s run has a "success" status
        success {
            script {
                def payload = """
{
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "themeColor": "0076D7",
    "summary": "Test Message",
    "sections": [{
        "activityTitle": "Test Message",
        "activitySubtitle": "",
        "activityImage": "https://cwiki.apache.org/confluence/download/attachments/30737784/oozie_47x200.png",
        "facts": [{
            "name": "ENVIRONMENT",
            "value": "${params.ENVIRONMENT}"
        }],
        "markdown": true
    }],
    "potentialAction": [{
        "@type": "OpenUri",
        "name": "View Build",
        "targets": [
            { "os": "default", "uri": "${BUILD_URL}" }
        ]
    }]
}"""
                // publish message to webhook
                httpRequest httpMode: 'POST',
                        acceptType: 'APPLICATION_JSON',
                        contentType: 'APPLICATION_JSON',
                        url: "${webhookUrl}",
                        requestBody: payload
            }
        }
    }

    // configure Pipeline-specific options
    options {
        // keep only last 10 builds
        buildDiscarder(logRotator(numToKeepStr: '10'))
        // timeout job after 60 minutes
        timeout(time: 60,
                unit: 'MINUTES')
    }

}
