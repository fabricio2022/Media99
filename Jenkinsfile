pipeline{
	agent{label 'master'}
	stages{
		stage('Checkout'){
			steps{
				git branch: 'vault', url: 'https://github.com/fabricio2022/Media99.git'
			}
		}
    		stage('Setup'){
      			steps{
				sh 'chmod +x install.sh'
        			sh './install.sh'
      			}
    		}
    		stage('Test'){
      			steps{
				 sh '''#!/bin/bash
				     source myprojectenv/bin/activate	
                		     python -m unittest
				     '''
               			}
   		}
		stage('invoke playbook'){
      			steps{
				ansiblePlaybook credentialsId: 'super', disableHostKeyChecking: true, inventory: '/home/fabricio', installation: 'AnsibleSuper', playbook: './app_playbook.yml', vaultCredentialsId: 'VaultID1'               			}
   		}
	}
}
