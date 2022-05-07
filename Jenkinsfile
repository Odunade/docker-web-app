Pipeline {

    any agent

    stages {

        stage("build")  {

            steps   {
                script{
                    echo 'building the application...'
                }

            }

        }

        stage("test")   {

            steps   {
                script{
                    echo  'testing the application...'
                }
                
            
            }

        }
        
        stage("deploy") {

            steps   {
                script{
                    def dockerCMD = 'docker run -p 3080:3080 -d odunade/my-app:2.0'
                    sshagent(['docker']) {
                        sh "ssh -o StrictHostKeyChecking=no ubuntu@52.55.188.212 ${dockerCMD}"
                    }
                
                }
                
            
            }
        }
    }
}
