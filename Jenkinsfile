pipeline{
    //agent anys
    agent {label 'worker'}
    options{
        buildDiscarder(logRotator(daysToKeepStr: '7'))
        disableConcurrentBuilds()
        timeout(time: 30, unit: 'MINUTES')
        retry(3)
    }
    parameters{
        string(name: 'BRANCH', defaultValue: 'master')
        booleanParam(name: 'UnitTestCases', defaultValue: false)
        choice(name: 'Environment', choices: ['Dev', 'QA', 'Uat', 'Prod'])
    }
    triggers{
        
        cron('H */5 * * *')
        pollSCM('H */5 * * *')
    }
    stages{
        stage("First Stage"){
            steps{
                sh "echo Helloooo"
                sh "sleep 10"
            }
        }
        stage("Second Stage"){
            steps{
                sh "echo Helloooo"
            }
            
        }
        
    }
    post
    {
       always
        {
            echo "Run always"
        }
        failure
        {
           echo "Failed"   
        }
        
    }
    
}
