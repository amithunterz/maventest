pipeline{
agent any
stages{
stage('compile stage'){
steps{
withMaven(maven : 'maven_3_6_0'){
bat 'mvn clean compile'}
}
}
stage('testing stage'){
steps{
withMaven(maven : 'maven_3_6_0'){
bat 'mvn test'}
}
}
stage('package stage'){
steps{
withMaven(maven : 'maven_3_6_0'){
bat 'mvn package'}
}
}

}
}