node {

    checkout scm

    env.DOCKER_API_VERSION="1.23"

    sh "git rev-parse --short HEAD > commit-id"

    tag = readFile('commit-id').replace("\n", "").replace("\r", "")
    appName = "countly-server"
    registryHost = "127.0.0.1:30400/"
    imageName = "${registryHost}${appName}:${tag}"
    env.BUILDIMG=imageName

    stage "Build"
        sh "echo ${imageName}"
        sh "docker build -t hdtrd/countly-server ."

    stage "Push"

        sh "docker login -p wangjunfeng -u hdtrd"
        sh "docker push hdtrd/countly-server"

    stage "Deploy"

}