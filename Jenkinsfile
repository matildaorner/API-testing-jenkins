pipeline {
    environment {
            PATH = "C:\\WINDOWS\\SYSTEM32;%JAVA_HOME%\\bin"
    }
    agent any
    
    stages{
        stage('Run Jmeter tests') {
            steps {
                bat '%JMETER_HOME%\\bin\\jmeter.bat -Jjmeter.save.saveservice.output_format=xml -n -t %JMETER_HOME%\\bin\\PerformanceTest\\Project_PrestaShop.jmx -l jmeter_report.jtl'
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