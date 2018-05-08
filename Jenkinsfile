#!/usr/bin/env groovy

pipeline {
    agent any
        parameters {
            choice(
                name: 'Nodes',
                choices:"Linux\nMac",
                description: "Choose Node!")
            choice(
                name: 'Versions',
                choices:"3.4\n4.4",
                description: "Build for which version?" )
            string(
                name: 'Path',
                defaultValue:"/home/pencillr/builds/",
                description: "Where to put the build!")
    }
    stages {
        stage("build") {
            steps {
                script {
                    build(job: "builder-job",
                        parameters:
                        [string(name: 'Nodes', value: "${params.Nodes}"),
                        string(name: 'Versions', value: "${params.Versions}"),
                        string(name: 'Path', value: "${params.Path}")])
                }
            }
        }
    }
}
