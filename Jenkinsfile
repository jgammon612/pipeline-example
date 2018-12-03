node('') {
stage 'buildInDevelopment'
openshiftBuild(namespace: 'dev', buildConfig: 'pythonscorecard', showBuildLogs: 'true')
stage 'deployInDevelopment'
openshiftDeploy(namespace: 'dev', deploymentConfig: 'pythonscorecard')
openshiftScale(namespace: 'dev', deploymentConfig: 'pythonscorecard',replicaCount: '2')
stage 'deployInTesting'
openshiftTag(namespace: 'dev', sourceStream: 'pythonscorecard',  sourceTag: 'latest', destinationStream: 'pythonscorecard', destinationTag: 'promoteToQA')
openshiftDeploy(namespace: 'qa', deploymentConfig: 'pythonscorecard', )
openshiftScale(namespace: 'qa', deploymentConfig: 'pythonscorecard',replicaCount: '3')
}
