#!/usr/bin/env groovy

def label = "k8s-${UUID.randomUUID().toString()}"
def home = "/home/jenkins"
def workspace = "${home}/workspace/build-jenkins-operator"
def workdir = "${workspace}/src/github.com/infrawatch/temp-cicd/"

podTemplate(label: label,
        containers: [
                containerTemplate(name: 'fedora', image: 'quay.io/fedora/fedora:34-x86_64', ttyEnabled: true, command: 'cat'),
        ],
        ) {
    node(label) {
        stage('Checkout code') {
            container('fedora') {
                checkout scm
                withEnv(["PATH+OC=${tool 'oc'}"]) {
                    openshift.withCluster() {
                        openshift.withProject( 'service-telemetry-ci' ) {
                            echo "${openshift.raw( "status" ).out}"
                            echo "In project: ${openshift.project()}"
                        }
                    }
                }
                sh 'ls -lah'
            }
        }
    }
}
