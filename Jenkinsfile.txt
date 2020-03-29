pipeline{
agent any
stages{
stage('compile stage'){
steps{
bat 'mvn clean compile'
}
}
stage('testing stage'){
steps{
bat 'mvn test'
}
}
stage('deployment stage'){
steps{
bat 'mvn deploy'
}
}

}
}