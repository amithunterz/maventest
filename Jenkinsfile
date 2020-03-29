pipeline{
agent any
stages{
stage('compile stage'){
steps{
bat 'mvn clean compile'}
}

stage('Sonar analysis'){
steps{
withSonarQubeEnv(credentialsId: 'alphasonar') {
    sonar.projectKey=sonarpipelinetest
sonar.projectName=sonarpipelinetest
}}}


stage('testing stage'){
steps{

bat 'mvn test'}

}
stage('package stage'){
steps{

bat 'mvn package'}

}

}
}