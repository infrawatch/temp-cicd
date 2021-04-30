pipelineJob('k8s-e2e') {
    displayName('temp-cicd main job')

    logRotator {
        numToKeep(10)
        daysToKeep(30)
    }

    configure { project ->
        project / 'properties' / 'org.infrawatch.plugins.workflow.job.properties.DurabilityHintJobProperty' {
            hint('PERFORMANCE_OPTIMIZED')
        }
    }

    definition {
        cpsScm {
            scm {
                git {
                    remote {
                        url('https://github.com/infrawatch/temp-cicd.git')
                    }
                    branches('*/main')
                }
            }
            scriptPath('cicd/pipelines/k8s.jenkins')
        }
    }
}

