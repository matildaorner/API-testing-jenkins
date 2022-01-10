pipeline {
    environment {
            PATH = "C:\\WINDOWS\\SYSTEM32;%JAVA_HOME%\\bin"
    }
    agent {    label 'Grupp1JMeter'    }
    
    stages{
        stage('Run Jmeter tests') {
            steps {
                bat 'C:\\programming_tools\\apache-jmeter-5.5-SNAPSHOT\\bin\\jmeter.bat -Jjmeter.save.saveservice.output_format=xml -n -t C:\\programming_tools\\apache-jmeter-5.5-SNAPSHOT\\bin\\PrestashopTestplan.jmx -l jmeter_report.jtl'
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