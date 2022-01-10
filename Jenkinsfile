pipeline {
    environment {
            PATH = "C:\\WINDOWS\\SYSTEM32;C:\\%JAVA_HOME%\\bin"
    }
    agent any
    
    stages{
        stage('Run Jmeter tests') {
            steps {
                bat 'C:\\%JMETER_HOME%\\bin\\jmeter.bat -Jjmeter.save.saveservice.output_format=xml -n -t C:\\%JMETER_HOME%\\bin\\PerformanceTest\\Project_PrestaShop.jmx -l jmeter_report.jtl'
                perfReport 'jmeter_report.jtl'
            }
        }
    }
    post {
        success {
            junit 'target/surefire-reports/**/*.xml'                       
        }
    }
}