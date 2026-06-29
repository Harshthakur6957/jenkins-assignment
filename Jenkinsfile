pipeline
{
environment
{
DOCKER_CRED = credentials('DockerHub')
}
agent any
stages
{
stage('fetch-code')
{
steps
{
git branch:'main', url:'https://github.com/Harshthakur6957/jenkins-assignment.git'
}
}
stage('build-image')
{
steps
{
sh 'docker build -t cheaterkook/jenkins-assignment:${BUILD_NUMBER} .'
}
}
stage('push-image') {
 steps {
 sh 'echo $DOCKER_CRED_PWS | docker login -u $DOCKER_CRED_USR --password-stdin'
sh 'docker push cheaterkook/jenkins-assignment:${BUILD_NUMBER}'
}
}
stage('update-image'){
steps
{
sh 'kubectl set image deployment/ja1 jenkins-assignment=cheaterkook/jenkins-assignment:${BUILD_NUMBER}'
}
}
}
}
