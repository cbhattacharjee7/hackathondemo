pipeline {
  agent any
  stages {
    stage('Test'){
    steps {
         withEnv(["JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_341.jdk/Contents/Home", "PATH=/Library/Java/JavaVirtualMachines/jdk1.8.0_341.jdk/Contents/Home/bin:$PATH"])
        {
        sh 'java -version'
        sh '/Applications/apache-maven-3.6.3/bin/mvn -e -X clean test' 
      }
    }
    }
    stage('Deploy') { 
      environment {

             ANYPOINT_CREDENTIALS = credentials('anypointPlatform')

            }
      steps {
         withEnv(["JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_341.jdk/Contents/Home", "PATH=/Library/Java/JavaVirtualMachines/jdk1.8.0_341.jdk/Contents/Home/bin:$PATH"])
        {
        sh 'java -version'
        sh '/Applications/apache-maven-3.6.3/bin/mvn -e -X clean deploy -DmuleDeploy -DskipTests -DconnectedAppClientId=${ANYPOINT_CREDENTIALS_USR} -DconnectedAppClientSecret=${ANYPOINT_CREDENTIALS_PSW} -Dcps.prefix=uat -Dcps.configServerBaseUrl=https://ei-sapi-aws-config-property-uat-v2.us-w2.cloudhub.io/api/v2 -Dcps.clientSecret=C46843688b9147A0b87B56DCf512483B -Dcps.projectName=hackathon-non-secure -Dcps.clientId=d7fb951a6bb344a0bb8882ffa09c0d89' 
      }
    }
  }
}
}
