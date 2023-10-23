pipeline {
    agent any
    tools {
        maven "MAVEN3"
        jdk "OracleJDK8"
    }
    environment { // all the variables from settings.xml & pom.xml
        SNAP_REPO = 'vprofile-snapshot'
        NEXUS_URL = 'admin'
        NEXUS_PASS = 'admin123'
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vpro-maven-central'
        NEXUSIP = '192.168.12.5'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUS_LOGIN = 'nexuslogin'

    }

    stages {
        stage('Build') {
             steps {
                sh 'mvn -s settings.xml -DskipTests install'  // mvn install skipping unit test & passing settings from settingx.xml
// we want maven to download dependencies from nexus & that is specified in pom.xml repositories section which contains nexus group repository URL
// to download these dependencies nexus needs other details like proxy repository URL, username & password all these details are mentioned in settings.xml                
// settings.xml contains all repositories information created in nexus, in the mirrors of settings.xml we see group repository URL
// Maven is going to look for repository in URL of pom.xml repository section & for dependencies it is going to look for group URL in mirrors of settings.xml

             }
        }
    }
}