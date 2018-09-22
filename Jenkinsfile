node {
stage('Scm Checkout'){
git credentialsId: 'git', url: 'https://github.com/kishanpeddaboina/aws-terraform'

}

   // Get the Terraform tool.
   def tfHome = tool name: 'terraform', type: 'org.jenkinsci.plugins.terraform.TerraformInstallation'
   env.PATH = "${tfHome}:${env.PATH}"
 
stage('TF Plan') {
      steps {
        container('terraform') {
          sh 'terraform init'
          sh 'terraform plan -out myplan'
        }
      }      
    }
stage('TF Apply') {
      steps {
        container('terraform') {
          sh 'terraform apply -input=false myplan'
        }
      }
    }
}
