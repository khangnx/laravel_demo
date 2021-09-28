node {
    currentBuild.result = "SUCCESS"
    try {
        stage('preparation'){
                //checkout scm
                git credentialsId: 'khangnx', url: 'https://github.com/khangnx/laravel_demo.git'
            }
            stage("composer_update") {
                // Run composer update
                bat 'composer update'
            }
            stage("unittest") {
                // Run PHPUnit
                bat 'vendor/bin/phpunit'
            }
    }
    catch (err) {
            currentBuild.result = "FAILURE"
                mail body: "project build error is here: ${env.BUILD_URL}" ,
                from: 'info@vnsys.wordpress.com',
                replyTo: 'info@vnsys.wordpress.com',
                subject: 'project build failed',
                to: 'keepwalking86@vnsys.wordpress.com'
            throw err
        }    
}