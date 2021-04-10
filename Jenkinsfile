@Library('shared-library@master') _
pipeline {
    agent any
environment {
        JFROG_ID = credentials('jfrogid')
       // bn = "${BUILD_NUMBER}"
      }
     parameters {
        string( name: 'buildnum')
    }
    stages {
        stage('Hello') {
            steps {
                echo " job name is ${env.JOB_NAME}"
            }
        }
        stage("Using curl example") {
            steps {
                script {
                    final String url = "https://jfrgfreetst.jfrog.io/artifactory/api/storage/example-repo-local/?sort"

                   

                  print(curlmethod(url,JFROG_ID,buildnum))
                      //print(foldcurlmethod(url,JFROG_ID,bn))
                }
            }
        }
    }
}

//def curlmethod(String url, String JFROG_ID,int bn ) {

//String resp = sh(script: "curl -u $JFROG_ID -s $url | grep uri | awk '{ print \$3 }' | sed 's+\"++g' | sed 's+/++g' | sed 's+,++g' | head -1", returnStdout: true).trim()

//return resp
 //String lt
   // if(bn > 1){
     //   lt = sh(script: "curl -u $JFROG_ID -s $url | grep uri |awk '{print \$3}'| sed 's+\"++g' | sed 's+/++g' | sed 's+,++g' | head -$bn | tail -1", returnStdout: true).trim();
    //}else{
      //  lt = sh(script: "curl -u $JFROG_ID -s $url | grep uri |awk '{print \$3}'| sed 's+\"++g' | sed 's+/++g' | sed 's+,++g' | head -$bn", returnStdout: true).trim();
    //}
    
    //return lt

//}

