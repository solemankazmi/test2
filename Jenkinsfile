pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git url: 'https://gitlab.com/solemankazmi/test.git', branch: 'hello'
            }
        }
        stage('deploy'){
steps {
            sh '''
#!/bin/bash
sole=$(ps ax | grep 'api.py' | grep -v grep | awk '{print $1}')
RESULT=$?
if [ $RESULT -ne 0 ]; then
kill -9 $sole
fi
export JENKINS_NODE_COOKIE=dontKillMe
ls
echo $PATH
echo $HOME
. /home/soleman/anaconda3/bin/activate tensor2
conda activate tensor2
nohup python api.py > log.txt 2>&1 &

            '''
        }
        }
    }
}

