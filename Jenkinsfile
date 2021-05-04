node('master') {
    checkout scm
    stage('approval') {
        timeout(time: 30, unit: 'DAYS') {
                input message: "Start first rollout ?"
            }
    }
    stage('hello world') {
        openshift.withCluster() {
            openshift.withProject( 'myproject' ) {
                echo "Hello from project ${openshift.project()} in cluster ${openshift.cluster()}"
            }
        }
    }
}
