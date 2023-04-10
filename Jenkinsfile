#!groovy 
// Build Parameters
properties([ parameters([ 
string( name: 'AWS_ACCESS_KEY_ID', defaultValue: 'AKIASYIIRCL7RPGNMENI'), 
string( name: 'AWS_SECRET_ACCESS_KEY', defaultValue: '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') 
]), pipelineTriggers([]) ]) 
// Environment Variables 
env.AWS_ACCESS_KEY_ID = AWS_ACCESS_KEY_ID 
env.AWS_SECRET_ACCESS_KEY = AWS_SECRET_ACCESS_KEY
node { 
env.PATH += ":/opt/terraform_0.14.5/" 
stage ('Checkout') { 
git branch: 'master', 
credentialsId: '0c595df8-4559-48fd-9292-59b5a1ace599', 
url: 'https://github.com/vikash-kumar01/TerraformScript-EKS.git' 
} 
stage ('Terraform Plan') { 
sh 'terraform init /var/lib/jenkins/workspace/terraform-lab-Pipeline' 
sh 'terraform plan /var/lib/jenkins/workspace/terraform-lab-Pipeline' 
} 
stage ('Terraform Apply') { 
sh 'terraform apply -auto-approve /var/lib/jenkins/workspace/terraform-lab-Pipeline' 
} 
stage ('Terraform Destroy') {
sh 'terraform destroy -auto-approve /var/lib/jenkins/workspace/terraform-lab-Pipeline'
} 
}
