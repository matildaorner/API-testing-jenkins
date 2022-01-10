pipeline {
    environment {
            PATH = "C:\\WINDOWS\\SYSTEM32;${JAVA_HOME}\\bin"
    }
    agent {    label 'Grupp1JMeter'    }
    
    stages{
        stage('Run Jmeter tests') {
            steps {
                bat "${JMETER_HOME}\\bin\\jmeter.bat -Jjmeter.save.saveservice.output_format=xml -n -t ${JMETER_HOME}\\bin\\PrestashopTestplan.jmx -l jmeter_report.jtl"
                perfReport 'jmeter_report.jtl'
            }
        }
    }
    post {
        success {
            junit allowEmptyResults: true, testResults: "${WORKSPACE}/test-results/*.xml"                       
        }
    }
}