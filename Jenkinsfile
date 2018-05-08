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
                
           // print the details gathered from the approval
            echo "Node: ${params.Nodes}"
            echo "Versions: ${params.Versions}"
            echo "Path: ${params.Path}"
                
            }
        }
    }
}
