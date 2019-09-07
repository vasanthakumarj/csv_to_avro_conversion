pipeline {
	agent any
	environment {
		PYTHON_PATH="/home/vasanth/anaconda3/bin/python"
		PIPENV="/home/vasanth/anaconda3/bin/pipenv"
		GITTAG = sh(returnStdout:true, script:'git describe --exact-match $GIT_COMMIT || true').trim()
		echo ${GITTAG}
		}
	stages {
		stage('installing pipenv ') {
			steps {
             			echo 'creating virtual env'
				sh '${PYTHON_PATH} -m pip install --upgrade pipenv'
				sh '${PIPENV} --python ${PYTHON_PATH} install --dev'
				}
			
			}
		stage('link checking') {
			steps {
				echo 'static analysis'
				sh '${PIPENV} run python setup.py flake8'
			}
		}
                stage('create build') {
			steps {
				echo 'create build'
				sh '${PIPENV} run python setup.py sdist'
				}
					}
		}
}
