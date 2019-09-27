# Add a comment to see if building is automatic
# after adding the GitHook

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
