node('built-in')
{
   stage('Continuous Download')
   {
        git 'https://github.com/intelliqittrainings/maven.git'
   }
   stage('Continous Build')
   {
       sh 'mvn package'
   }
   stage('Contiouns Deployment')
   {
       deploy adapters: [tomcat9(credentialsId: 'b06da7ad-d66e-4792-819c-85d682f068a0', path: '', url: 'http://172.31.40.202:8080')], contextPath: 'testapp', war: '**/*.war'
   }
   stage('Continous Testing')
   {
       git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
       
       sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline/testing.jar'
   }
   stage('Continous Delivery')
   {
       input message: 'Need to approval from DM.', submitter: 'gayatri'
       
       deploy adapters: [tomcat9(credentialsId: 'b06da7ad-d66e-4792-819c-85d682f068a0', path: '', url: 'http://172.31.37.177:8080')], contextPath: 'prodapp', war: '**/*.war'
   }
   
}
