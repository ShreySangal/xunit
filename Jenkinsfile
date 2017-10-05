node 
{
    stage "Build"
        checkout scm
        sh 'npm install'
    
    stage "Test"
    
step([$class: 'XUnitBuilder', testTimeMargin: '3000', thresholdMode: 1,
    thresholds: [
        [$class: 'FailedThreshold', failureNewThreshold: '', failureThreshold: '', unstableNewThreshold: '', unstableThreshold: '1'],
        [$class: 'SkippedThreshold', failureNewThreshold: '', failureThreshold: '', unstableNewThreshold: '', unstableThreshold: '']],
    tools: [
        [$class: 'JUnitType', deleteOutputFiles: false, failIfNotNew: false, pattern: 'reports/**', skipNoTestFiles: false, stopProcessingIfError: true]]
    ])

// Equivalent xUnit step - cleaned
step([$class: 'XUnitBuilder',
    thresholds: [[$class: 'FailedThreshold', unstableThreshold: '1']],
    tools: [[$class: 'JUnitType', pattern: 'reports/**']]])
            //step([$class: 'SauceOnDemandTestPublisher'])
}
