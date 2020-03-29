pipeline{
agent any
stages{
stage('compile stage'){
steps{
withMaven(maven : 'Apache Maven 3.6.0'){
bat 'mvn clean compile'}
}
}
stage('testing stage'){
steps{
withMaven(maven : 'Apache Maven 3.6.0'){
bat 'mvn test'}
}
}
stage('package stage'){
steps{
withMaven(maven : 'Apache Maven 3.6.0'){
bat 'mvn package'}
}
}

}
}