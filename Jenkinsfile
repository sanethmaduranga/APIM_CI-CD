pipeline {

    agent {
        node {
            label 'master'
        }
    }
    // environment { 
    //     PATH = "/root/apictl:$PATH"
    // }
    options {
        buildDiscarder logRotator( 
                    daysToKeepStr: '16', 
                    numToKeepStr: '10'
            )
    }

    stages {

        // stage('Setup Environment for APICTL') {
        //     steps {
        //         sh """#!/bin/bash
        //         ENVCOUNT=\$(apictl list envs --format {{.}} | wc -l)
        //         if [ "\$ENVCOUNT" == "0" ]; then
        //             apictl add-env -e live --apim https://live.apis.com:9443
        //         fi
        //         """
        //     }
        // }

        stage('Deploy APIs To "prod" Environment') {
            steps {
                sh """
                apictl login prod -u admin -p admin
                apictl vcs deploy -e prod
                """
            }
        }
    }   
}