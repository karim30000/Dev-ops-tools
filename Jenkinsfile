pipeline{
    agent any
    stages{
        stage("CI"){
            steps{
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                sh """
                docker build . -f dockerfile -t karim3000/nodejsapp      
                docker login -u ${USERNAME} -p ${PASSWORD}
                docker push karim3000/nodejsapp
                """
                }
            }
        }
        stage("CD"){
            steps{
                sh "docker run -d -p 3000:3000 karim3000/nodejsapp"
            }
        }
    }
}
