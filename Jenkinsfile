pipeline {

    agent any

    stages {

    stage('Build') {

        steps {
                sh '''
                python3 --version
                python3 -m venv venv
                source venv/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt
                '''

        }

    }

    stage('Test') {

        steps {

        sh '''
        source venv/bin/activate
        pytest -v
        '''

    }

}
    stage('Deploy') {

        steps {

        sh '''
        source venv/bin/activate

        pkill -f "python3 app.py" || true

        nohup python3 app.py > flask.log 2>&1 &
        '''

    }

}
    }
}
