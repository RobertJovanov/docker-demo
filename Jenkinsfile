# This particular line is done after the assessment, just to check if everything is still in place 




# asfasfasfsaas  Add a comment to see if building is automatic
# after adding the GitHook
# Let's see if it worked after configuring the GitHub webhook

# Last try?

node{
    git credentialsId: 'rjgitcredentials', 
    url: 'https://github.com/RobertJovanov/docker-demo.git'
    
    stage('checkout'){
        checkout([$class: 'GitSCM', 
        branches: [[name: '*/master']], 
        doGenerateSubmoduleConfigurations: false, 
        extensions: [], 
        submoduleCfg: [], 
        userRemoteConfigs: [[url: 'https://github.com/RobertJovanov/docker-demo.git']]])
    }
    
    stage('build image'){
        docker.build('rjassessment')
    }
    
    stage('push image'){
        docker.withRegistry('https://473293451041.dkr.ecr.eu-central-1.amazonaws.com', 'ecr:eu-central-1:rjasessmentcredentials'){
            docker.image('rjassessment').push('assessmentimage')
        }
    }
}
