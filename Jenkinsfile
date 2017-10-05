node {
    stage "Build"
    checkout scm

    // Install dependencies
    sh 'npm install'

    stage "Test"
    // Add sauce credentials
    /*sauce('f0a6b8ad-ce30-4cba-bf9a-95afbc470a8a') {
        // Start sauce connect
        sauceconnect(options: '', useGeneratedTunnelIdentifier: false, verboseLogging: false) {

            // List of browser configs we'll be testing against.
            def platform_configs = [
                'chrome',
                'firefox',
                'ie',
                'edge'
            ].join(',')

            // Nightwatch.js supports color ouput, so wrap this step for ansi color
            wrap([$class: 'AnsiColorBuildWrapper', 'colorMapName': 'XTerm']) {
                // Run selenium tests using Nightwatch.js
                // Ignore error codes. The junit publisher will cover setting build status.
                sh "./node_modules/.bin/nightwatch -e ${platform_configs} || true"
            }*/

            //junit 'reports/**'
// Equivalent xUnit step - generated (reformatted)
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
    }
}
