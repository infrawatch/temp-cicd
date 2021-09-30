#!/usr/bin/env groovy

node {
    stage("One"){
        def local_branch = sh (
            script: "git rev-parse --abbrev-ref HEAD",
            returnStdout: true
            ).trim()
        println "Local branch is ${local_branch}"
        
        def git_diff = sh (
            script: "git diff --name-only HEAD~1",
            returnStdout: true
        ).trim()
        println git_diff
    }
}
