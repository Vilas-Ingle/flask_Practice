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
    }
}
