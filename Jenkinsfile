pipeline{
agent any
stages{
stage('compile stage'){
steps{
bat 'mvn clean compile'}
}

stage('Sonar analysis'){
steps{
	bat 'mvn sonar:sonar -Dsonar.projectKey=sonarpipelinetest -Dsonar.projectName=sonarpipelinetest -Dsonar.host.url=http://localhost:9000 -Dsonar.login=79940f09ee84c726b644ddeb9fcefad5db6020ad'
}
}


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