
#!/usr/bin/env groovy


node('master') {
    checkout scm
    stage('auto merge'){
        sh """
            git fetch origin
            git checkout -b ${env.BRANCH_NAME} origin/${env.BRANCH_NAME}
            git merge ${env.CHANGE_TARGET}
            git checkout ${env.CHANGE_TARGET}
            git merge --no-ff ${env.BRANCH_NAME}
            git push origin ${env.CHANGE_TARGET}
        """
    }
}
