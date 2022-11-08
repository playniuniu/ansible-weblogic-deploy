pipeline{
	agent any

	stages{
		stage(build) {
		steps {
			checkout scm
			script {
				tags = sh(script: "git tag --sort=v:refname | tail -5 ", returnStdout: true).trim()
                        	properties([
                             		parameters([
                                  		choice(
                                     			choices:"${tags}",
                                         		name: 'TAG'
                                         	),
                                       	])
                                   ])
				tagskit = sh(script: "git tag --sort=v:refname | tail -1 ", returnStdout: true).trim()
				sh "git checkout tags/${tagskit}"
				}
			}
		}
	}
}
