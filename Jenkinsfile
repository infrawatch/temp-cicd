#!/usr/bin/env groovy

node {
    stage("One"){
        
        def git_diff = sh (
            script: "git diff --name-only origin/aveselov-test..HEAD",
            returnStdout: true
        ).trim()
        println git_diff
    }
}
