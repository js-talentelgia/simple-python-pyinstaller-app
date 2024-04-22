pipeline{
    agent any
    stages{
        stage('Build'){
        steps{
            sh 'python3 -m py_compile sources/add2vals.py sources/calc.py'
            stash(name: 'compiled-results', includes: 'sources/*.py*')
            }
        }
        stage('Test') {
        steps {
            sh 'sudo /home/ubuntu/.local/lib/python3.10/site-packages/pytest --junit-xml test-reports/results.xml sources/test_calc.py'
        }
        post {
            always {
                junit 'test-reports/results.xml'
            }
        }
    }
    }
}