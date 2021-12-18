pipeline {
    agent {
        docker { image 'node:16.13.1-alpine' }
    }
  
	stages {
        stage('NPM') {
            steps {
                sh 'node --version'
                sh 'npm ci'
            }
        }
		stage('UnitTests & Coverage') {
			steps {
				echo "Unit Tests"
				sh 'npm test'
			}		
		}
		stage('Static Code Analysis') {

			steps {
				echo "SCA"
			}
		}

		stage('Build') {
			steps {
				echo "Build"
				sh 'npm build'
				//archiveArtifacts(artifacts: 'dist', onlyIfSuccessful: true, fingerprint: true)
			}
		}
		stage('Docker Image') {
			steps {
				echo "Docker Image"
			}
		}
		stage('EKS-Deployment') {
			steps {
				//kubernetesDeploy configs: 'eks-deployment.yaml', kubeConfig: [path: ''], kubeconfigId: 'eks-kubeconfig', secretName: '', ssh: [sshCredentialsId: '*', sshServer: ''], textCredentials: [certificateAuthorityData: '', clientCertificateData: '', clientKeyData: '', serverUrl: 'https://']
				echo "GKE-Deployment"
			}
		}
	}
}
