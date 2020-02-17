@Library('KOSi Pipeline Library') _

def config = [
    slack : [
        channel : '#proj-moab-oulu',
        onlyOnFail : 'false'
    ]
]

pipeline
{
    agent any
    stages
    {
        stage('Prepare')
        {
            steps
            {
                echo "${STAGE_NAME}"                                
            }
        }
        stage('Parallel Build')
        {
            parallel()
            {
                stage('Build A')
                {
                    agent { label "vsbuild_bbn" }
                    stages
                    {
                        stage('Build')
                        {
                            steps
                            {
                                echo "${STAGE_NAME}"                                
                            }
                        }
                        stage('Test')
                        {
                            steps
                            {
                                echo "${STAGE_NAME}"                                
                            }
                        }
                    }
                }
                stage('Build B')
                {
                    stages
                    {
                        stage('Build')
                        {
                            steps
                            {
                                echo "${STAGE_NAME}"                                
                            }
                        }
                        stage('Test')
                        {
                            steps
                            {
                                echo "${STAGE_NAME}"                                
                            }
                        }
                    }
                }
            }
        }
        stage('Deploy')
        {
            steps
            {
                echo "${STAGE_NAME}"                                
            }
        }
		stage('slack')
        {
            steps
            {
                SendMessageToSlackViaJava(config, "hello slack")
            }
        }
    }
}