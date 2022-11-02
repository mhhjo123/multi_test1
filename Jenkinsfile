pipeline{
	agent any
	
	stages{
		stage('Build'){
			steps{
				echo 'Building...!'
				bat "javac src/HelloWorld.java"
			}
		}
		
		stage('Deploy'){
			steps{
				echo 'Deploying...'
				sshPublisher(
              publishers: 
              [sshPublisherDesc(
                  configName: 'Linux for Jenkins Test', 
                  transfers: 
                  [sshTransfer(
                      cleanRemote: false, 
                      excludes: '', 
                      execCommand: '''echo cd jenkins_test2/src > /root/jenkins_test2/master2_result.txt
                                      cd jenkins_test2/src 
                                      pwd >> /root/jenkins_test2/master2_result.txt
                                      echo HelloWorld.class execute >> /root/jenkins_test2/master2_result.txt
                                      java HelloWorld >> /root/jenkins_test2/master2_result.txt''', 
                      execTimeout: 120000, 
                      flatten: false, 
                      makeEmptyDirs: false, 
                      noDefaultExcludes: false, 
                      patternSeparator: '[, ]+', 
                      remoteDirectory: '', 
                      remoteDirectorySDF: false, 
                      removePrefix: '', 
                      sourceFiles: 'src/*.class')], 
                      usePromotionTimestamp: false, 
                      useWorkspaceInPromotion: false, 
                      verbose: true
              )
              ]
          )
			}
		}
	}
}