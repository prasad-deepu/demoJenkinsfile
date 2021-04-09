pipeline {
    agent any
environment {
        JFROG_ID = credentials('jfrogid')
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

                   

                  //print(curlmethod(url,JFROG_ID))
                      print(foldercurlmethod(url,JFROG_ID))
                }
            }
        }
    }
}

def curlmethod(String url, String JFROG_ID ) {

String resp = sh(script: "curl -u $JFROG_ID -s $url | grep uri | awk '{ print \$3 }' | sed 's+\"++g' | sed 's+/++g' | sed 's+,++g' | head -1", returnStdout: true).trim()

return resp

}

def foldercurlmethod(String url ,String JFROG_ID) {
    ArrayList<String[][]> lt = new ArrayList<>()
    //lt = sh(script: "curl -u $JFROG_ID -s $url | grep uri | awk '{ print \$3 }'| sed 's+\"++g' | sed 's+/++g' | sed 's+,++g'", returnStdout: true).trim()
    lt = sh(script: "curl -u $JFROG_ID -s $url | jq -r '.children[].uri' | sed 's+\"++g' | sed 's+/++g' | sed 's+,++g'", returnStdout: true).trim(
    
    return lt
}
