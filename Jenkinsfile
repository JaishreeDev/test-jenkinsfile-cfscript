pipeline {
   agent any

   environment {
      input_params = get_param()
      PATH = "C:\\WINDOWS\\SYSTEM32"
    }

   stages {
      stage('start') {
          //agent any
         steps {
            echo 'Hello World'
            //bat '%AWS_CLI_PATH%'
            bat "%AWS_CLI_PATH% configure list"
            bat "%AWS_CLI_PATH% cloudformation create-stack --stack-name S3BucketStack --template-body file://${workspace}//s3BucketCreation.json"
         }
      }

      stage('Variable') {
          steps {
            echo "Client: ${env.input_params}"
            echo "Workspace: ${workspace}"
          }
      }
   }
}

def get_param() {
    node('master') {
		return env.ENV
    }
}

/*def func() {
  sh 'aws configure list'

}*/
