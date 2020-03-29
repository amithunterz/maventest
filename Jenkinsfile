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


	stage('Publish'){
			rtUpload (
    serverId: 'ArtifactoryImage',
    spec: '''{
          "files": [
            {
              "pattern": "**/*.war",
              "target": "jenkins-local-maven-repo/"
            }
         ]
    }''',
 
    buildName: 'holyFrog',
    buildNumber: '42'
)
		
		rtDownload (
    serverId: 'ArtifactoryImage',
    spec: '''{
          "files": [
            {
              "pattern": "jenkins-local-maven-repo/",
              "target": "target/",
            }
          ]
    }''',

    buildName: 'holyFrog',
    buildNumber: '42'
)
	}	
		
		

	}


}