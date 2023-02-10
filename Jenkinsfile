pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/Yogendaroduru/JMeter-Exercises.git'
            }
        }
        stage('Execute JMeter') {
            steps {
            
                sh """
                cd /home/saikrishna/Downloads/apache-jmeter-5.5/bin/jmeter.sh -n -t "Test Plans/PetStore-End-to-End-Flow.jmx" -p "Test Plans/data/PetStore_LoadTest.properties" -JTOTAL_THREADS=2 -JTEST_DURATION=60 -l MyRun1.jtl -e -o index.html
                """
            
            }
        }
        stage('Publish Report') {
            steps {
            
                perfReport filterRegex: '', sourceDataFiles: '**/*.jtl'
            
            }
        }
    }
}
