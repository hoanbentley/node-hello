#!groovy
// @Library(['jenkins-shared-pipelines@pe-generator-pipeline']) _
// @Library(['jenkins-shared-pipelines@npm-local-registry']) _
@Library(['jenkins-shared-pipelines@npm-local-registry',
'jenkins-shared-libraries@npmLocalNpm'
]) _

appData=[
  binaryPath : "node-hello/target",
  nodeVersion: "18.18.2",
  jdkVersion: "17",
  mavenTestGoals: "test"
]

env.DEFAULT_JFROG_TOOL = "npm"
// env.DEFAULT_JFROG_TOOL = "artifactory-plugin"

if (env.BRANCH_NAME == "master") {
    echo "Production releases should go through release pipeline"
} else if (env.BRANCH_NAME == "integration") {
    promote(appData)
} else {
    dev_npmWithNodeModulesLocalReg(appData)
}
