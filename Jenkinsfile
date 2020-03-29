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
	
//		stage('package stage')
//		{
//			steps
//			{
//				bat 'mvn package'
//			}
//
//		}








stage ('Artifactory configuration') {



            steps {



                rtMavenDeployer (



                    id: "MAVEN_DEPLOYER",



                    serverId: "ArtifactoryImage",



                    releaseRepo: "jenkins-local-maven-repo",



                    snapshotRepo: "jenkins-local-maven-repo"



                )







                rtMavenResolver (



                    id: "MAVEN_RESOLVER",



                    serverId: "ArtifactoryImage",



                    releaseRepo: "jenkins-local-maven-repo",



                    snapshotRepo: "jenkins-local-maven-repo"



                )



            }



        }







        stage ('Exec Maven') {



            steps {



                rtMavenRun (



                    tool: "maven_3_6_0", // Tool name from Jenkins configuration



                    pom: 'pom.xml',



                    goals: 'clean package',



                    deployerId: "MAVEN_DEPLOYER",



                    resolverId: "MAVEN_RESOLVER"



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












//	stage('Upload'){
//		steps{
//			rtUpload (
 //   serverId: 'ArtifactoryImage',
 //   spec: '''{
  //        "files": [
 //           {
 //             "pattern": "**/*.war",
 //             "target": "jenkins-local-maven-repo/"
 //           }
 //        ]
 //   }''',
// 
//    buildName: 'holyFrog',
//    buildNumber: '42'
//)}}

//stage('Download'){
//steps{
//		
//		rtDownload (
//   serverId: 'ArtifactoryImage',
//    spec: '''{
//          "files": [
//            {
//              "pattern": "jenkins-local-maven-repo/",
//              "target": "target/"
//            }
//         ]
//    }''',
//
//    buildName: 'holyFrog',
//    buildNumber: '42'
//)
//	}
//}	
		
		

	}


}