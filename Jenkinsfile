podTemplate(name: "nodebuild", inheritFrom: 'jnlp', serviceAccount: 'serverspec-sa', label: "nodebuild", containers: [
  containerTemplate(name: 'nodegoat',
                    image: '1njected/nodegoat',
                    ttyEnabled: true,
                    command: 'cat',
                    resourceLimitCpu: '250m',
                    resourceRequestCpu: '250m',
                    resourceRequestMemory: '250Mi',
                    resourceLimitMemory: '250Mi',
                    alwaysPullImage: true,
                    ports: 4000),
  containerTemplate(name: 'mongo',
                    image: 'mongo',
                    ttyEnabled: true,
                    command: 'cat',
                    resourceLimitCpu: '250m',
                    resourceRequestCpu: '250m',
                    resourceRequestMemory: '250Mi',
                    resourceLimitMemory: '250Mi',
                    alwaysPullImage: true,
                    ports: 27017),
  containerTemplate(name: 'zap',
                    image: 'owasp/zap2docker-stable:2.6.0',
                    ttyEnabled: true,
                    command: 'cat',
                    resourceLimitCpu: '250m',
                    resourceRequestCpu: '250m',
                    resourceRequestMemory: '250Mi',
                    resourceLimitMemory: '250Mi',
                    alwaysPullImage: true)
])
{
  node("nodebuild") {
    // checkout scm

    stage("build") {
      container("nodegoat") {
        sh "curl http://localhost:4000"

        sh "curl http://localhost:27017"
      }
    }
  }
}
