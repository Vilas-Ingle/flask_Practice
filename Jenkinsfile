pipeline {

    agent any

    stages {

    stage('Build') {
    steps {
        sh '''
        python3 --version
        python3 -m venv venv

        ./venv/bin/pip install --upgrade pip
        ./venv/bin/pip install -r requirements.txt

        cat > .env <<EOF
MONGO_URI=mongodb+srv://mohan:Herovired123@herovired.f3do4.mongodb.net/studentDB
SECRET_KEY=your-secret-key
EOF
        '''
    }
}

    stage('Test') {
    steps {
        sh '''
        ./venv/bin/pytest -v
        '''
    }
}
    stage('Deploy') {
    steps {
        sh '''
        pkill -f "python3 app.py" || true
        nohup ./venv/bin/python app.py > flask.log 2>&1 &
        '''
    }
}

    post {
    success {
        mail to: 'vilasaingle@gmail.com',
             subject: "SUCCESS: Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
             body: "Good News! Job Name: ${env.JOB_NAME} Build Number: ${env.BUILD_NUMBER}\nThe Jenkins pipeline completed successfully.\n\nRegards,\nJenkins"
    }
    failure {
        mail to: 'vilasaingle@gmail.com',
             subject: "FAILED: Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
             body: "Attention! Job Name: ${env.JOB_NAME} Build Number: ${env.BUILD_NUMBER}\nThe Jenkins pipeline has failed. Please check Jenkins console output.\n\nRegards,\nJenkins"
    }
}

    }
}
