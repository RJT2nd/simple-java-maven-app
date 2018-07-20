pipeline {
	agent {
		docker {
			image 'maven:3-alpine'
			args '-v /root/.m2:/root/.m2'
		}
	}
	stages {
		stage('Build') {
			steps {
				sh 'mvn -B -DskipTests clean package'
			}
		}
		stage('Test') {
			steps {
				sh 'mvn test'
			}
			post {
				always {
					junit 'target/surefire-reports/*.xml'
				}
			}
		}
		step([$class: 'AWSCodeDeployPublisher', applicationName: 'JenkinsCodeDeploy-DemoApplication-1VKI02XE9YGEL', awsAccessKey: '', awsSecretKey: <object of type hudson.util.Secret>, credentials: 'iamRoleArn', deploymentConfig: 'CodeDeployDefault.OneAtATime', deploymentGroupAppspec: false, deploymentGroupName: 'JenkinsCodeDeploy-DemoFleet-1WHIJVXQW3BWH', excludes: '', iamRoleArn: 'arn:aws:iam::345220119325:role/JenkinsCodeDeploy-JenkinsCodeDeployRole-EB21UY8RTHVS', includes: '**', proxyHost: '', proxyPort: 0, region: 'us-east-1', s3bucket: 'jenkinscodedeploy-codedeploybucket-1mlkkcjdbfzel', s3prefix: '', subdirectory: '', versionFileName: '', waitForCompletion: false])
	}
}
