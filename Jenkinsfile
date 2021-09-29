node {

    stage ('Clone') {
        git url: 'https://github.com/sonar-scanning-examples.git'
    }

    stage ('Prebuild') {
	echo "Prebuild"
    }


    stage ('Build') {
        sh -c "cd sonarqube-scanner-maven; mvn clean install sonar:sonar"
	
    }

    stage ('PostBuild') {
        sh -c "export WAIT_FOR_ANALYSIS=true; ./sonarqube/artifactory/artifactory-sonar.sh true"
    }

    stage ('Staging') {
        echo "Promoted to Staging"
    }

}

