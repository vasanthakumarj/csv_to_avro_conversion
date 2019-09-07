pipeline {
	agent any
	environment {
		PYTHON_PATH="/home/vasanth/anaconda3/bin/python"
		GITTAG = sh(returnStdout:true, script:'git describe --exact-match $GIT_COMMIT || true').trim()
		}
	stages {
		stage('installing pipenv ') {
			steps {
             			echo 'creating virtual env'
				sh '${PYTHON_PATH} -m pip install --upgrade --pipenv'
				sh 'pipenv --python ${PYTHON_PATH} install --dev'
				}
			
			}
                stage('create build') {
			steps {
				echo 'create build'
				sh 'pipenv run python setup.py sdist'
				}
					}
		}
}
