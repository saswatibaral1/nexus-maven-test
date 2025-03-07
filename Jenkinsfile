pipeline{
 tools{
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }
     agent any
	  
	  stages{
	  
	  stage("checkout"){
	   steps{
	   git 'https://github.com/saswatibaral1/nexus-maven-test.git'
	   }
	                  }
	
	   stage("compile"){
	    steps{
		 sh 'mvn compile'
		}
		}
       stage("test"){
	    steps{
		 sh 'mvn test'
		}
		}
	
       stage("package"){
	    steps{
		 sh 'mvn clean package'
                 sh "mv target/*.jar target/mywebapp.jar"

		}
		}
stage(backup)
		  {
  steps{

	nexusArtifactUploader artifacts: [[artifactId: 'webapp-1', classifier: '', file: 'target/mywebapp.jar', type: 'jar']], credentialsId: 'nexus', groupId: 'com.idreamsitsolutions', nexusUrl: '13.234.76.9:8081/repository/maven-snapshots/', nexusVersion: 'nexus2', protocol: 'http', repository: 'maven-snapshots/', version: 'SNAPSHOTS1.0'
	  
  }
	
}
	}
	}
