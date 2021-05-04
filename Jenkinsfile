node('master') {
    withEnv(["PATH+OC=${tool 'oc'}"]) {
        openshift.withCluster() {
            echo "${openshift.raw( "version" ).out}"
            echo "In project: ${openshift.project()}"
        }
    }
}
