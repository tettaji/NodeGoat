def container_name = "base"
def tag_name = "kpnappfactory/${container_name}"

podTemplate(name: "nodebuild", inheritFrom: 'jnlp', serviceAccount: 'serverspec-sa', label: "nodebuild", containers: [
  containerTemplate(name: 'node',
                    image: 'node:4',
                    ttyEnabled: true,
                    command: 'cat',
                    resourceLimitCpu: '250m',
                    resourceRequestCpu: '500m',
                    resourceRequestMemory: '250Mi',
                    resourceLimitMemory: '500Mi',
                    alwaysPullImage: true)])
{
  node("nodebuild") {
    checkout scm

    stage("build") {
      sh "npm install"

      sh "docker build ."
    }
  }
}
