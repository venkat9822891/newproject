node {
    stage('Cont.Download') {
    git 'https://github.com/venkat9822891/newproject.git'
                            }
    stage('Cont.Build') {
    sh 'mvn  clean package'
                        }
    stage('Cont.Deploy') {
    deploy adapters: [tomcat9(credentialsId: '0ed97821-79ef-477f-90b5-82cf4a3ab55e', path: '', url: 'http://172.31.9.104:8080')], contextPath: '/devapp', war: '**/*.war'
                          }
}
