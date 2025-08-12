pipeline {
    agent any
    
    tools {
        maven 'my-maven'  // 젠킨스에서 설치한 이름
    }

    stages {
        stage('0. 자동화 확인1(제발요)') { steps { echo '스테이지 출발' } }
        /*
        stage('1. Build') {
            steps {
                echo 'Maven으로 빌드 시작'
                sh 'mvn clean package'
            }
        }
        
        stage('2. Check Docker') {
            steps {
                sh 'docker version'
            }
        }
        
        stage('3. Docker Build') {
            steps {
                sh 'docker build -t ex02-app:latest .'
            }
        }

        stage('4. Docker Push') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-cred',
                    usernameVariable: 'DOCKERHUB_USERNAME',
                    passwordVariable: 'DOCKERHUB_PASSWORD'
                )]) {
                    sh '''
                    echo "$DOCKERHUB_PASSWORD" | docker login -u "$DOCKERHUB_USERNAME" --password-stdin
                    docker tag ex02-app:latest $DOCKERHUB_USERNAME/ex02-app:latest
                    docker push $DOCKERHUB_USERNAME/ex02-app:latest
                    '''
                }
            }
        }
        */
        /*
        stage('5. Deploy to K3s') {
            steps {
                sh '''
                export KUBECONFIG=/home/vagrant/.kube/config
                kubectl apply -f k8s-deployment.yaml
                '''
            }
        }
        */
        

        stage('6. Deploy with Helm') {
            steps {
                sh '''
                export KUBECONFIG=/home/vagrant/.kube/config                
                helm upgrade --install ex01-app ./charts/ex01-app --namespace default
                '''
            }
        }        

    }
}

