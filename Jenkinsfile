node('master') {
    withEnv(["PATH+OC=${tool 'oc'}"]) {
        openshift.withCluster() {
            echo "${openshift.raw( "status" ).out}"
            echo "In project: ${openshift.project()}"
        }
    }
}
