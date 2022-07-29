// node{

//     stage('SCM Checkout')
//     {
//         git credentialsId: '4cc785e9-441d-4818-a248-2bfb2148004d', url: 'https://github.com/VardhanNS/phpmysql-app.git'
//     }
    
//     stage('Run Docker Compose File')
//     {
//         echo 'sudo docker-compose build'
//         echo 'sudo docker-compose up -d'
//     }
//   stage('PUSH image to Docker Hub')
//     {
//       /* withCredentials([string(credentialsId: 'DockerHubPassword', variable: 'DHPWD')]) 
//         {
//             sh "docker login -u upasanatestdocker -p ${DHPWD}"
//         }
//         echo 'docker push vardhanns/phpmysql_app'
//         */
//         docker.withRegistry( 'registry.docker.io', 'DockerHubPassword', 'docker-hub-credentials' ) {
//              dockerImage.push()
//              echo 'sudo docker login -u "beckfee" -p "024161408" docker.io'
//              //sh 'sudo docker push beckfee/mysql'
//              //sh 'sudo docker push beckfee/job1_web1.0'
//              echo 'sudo docker push beckfee/sampleonline-shop:online-shopV.1'
//             // sh 'docker push upasanatestdocker/mysql'
          
//     }
// }



node {

  checkout scm
  def dockerImage

  stage('Build image') {
    dockerImage = docker.build("beckfee/sampleonline-shop:sampleonline-shopV1")
  }

  stage('Push image') {
    docker.withRegistry('registry.docker.io', 'docker-hub-credentials') {
      dockerImage.push()
    }
  }

}
