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

                    // final String response = sh(script: "curl -u prasad.mr@dxc.com:Mrp1234\$ -s $url | grep uri | awk '{ print $3 }' | sed s/\"//g | sed 's+/++g' | sed 's+,++g' |head  -1", returnStdout: true).trim()
                //final String response = sh(script: "curl -u prasad.mr@dxc.com:Mrp1234\$ -s $url | grep uri | awk '{ print \$3 }' | sed 's+\"++g' | sed 's+/++g' | sed 's+,++g' | head -1", returnStdout: true).trim()

                  print(curlmethod(url,JFROG_ID))
                }
            }
        }
    }
}

def curlmethod(String url, String JFROG_ID ) {

String resp = sh(script: "curl -u $JFROG_ID -s $url | grep uri | awk '{ print \$3 }' | sed 's+\"++g' | sed 's+/++g' | sed 's+,++g' | head -1", returnStdout: true).trim()

return resp

}
