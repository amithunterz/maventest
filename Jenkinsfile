pipeline
{
	agent any
	stages
	{
		stage('compile stage')
		{
			steps
			{
				bat 'mvn clean compile'
			}
		}

		stage('Sonar analysis')
		{
			steps
			{
				bat 'mvn sonar:sonar -Dsonar.projectKey=sonarpipelinetest -Dsonar.projectName=sonarpipelinetest -Dsonar.host.url=http://localhost:9000 -Dsonar.login=79940f09ee84c726b644ddeb9fcefad5db6020ad'
			}
		}


		stage('testing stage')
		{
			steps
			{
				bat 'mvn test'
			}
		}
	
		stage('package stage')
		{
			steps
			{
				bat 'mvn package'
			}
		}
		
		stage ('Artifactory configuration') {
            steps {
                rtMavenDeployer (
                    id: "MAVEN_DEPLOYER",
                    serverId: "ArtifactoryImage",
                    releaseRepo: "jenkins-local-maven-repo",
                    snapshotRepo: "jenkins-local-maven-repo"
                )
            }
        }

        stage ('Artifactory Exec Maven') {
            steps {
                rtMavenRun (
                    tool: "maven_3_6_0", // Tool name from Jenkins configuration
                    pom: 'pom.xml',
                    goals: 'clean package',
                    deployerId: "MAVEN_DEPLOYER",
                )
            }
        }
        stage ('Publish build info') {
            steps {
                rtPublishBuildInfo (
                    serverId: "ArtifactoryImage"
                )
            }
        }
		stage('Deploy'){
			steps{
				deploy adapters: [tomcat8(credentialsId: 'd4b2f316-0750-49d2-9718-5fe4afc3f1c5', path: '', url: 'http://localhost:8086/')], contextPath: 'my-demo-app', onFailure: false, war: '**/*.war'
				bat 'start http://localhost:8086/mt-demo-app'
			}
		}	
	}
}