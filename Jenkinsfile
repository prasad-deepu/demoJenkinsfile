//@Library('shared-library@master') _
pipeline {
    agent any
environment {
        JFROG_ID = credentials('jfrogid')
       //bn = "${BUILD_NUMBER}"
    url = "https://jfrgfreetst.jfrog.io/artifactory/api/storage/example-repo-local"
    folder_path = curlmethod(url,JFROG_ID,buildnum)
    Path = "${url}/${folder_path}/?sort"
   image_name = curlmethodnew(Path, JFROG_ID)
      }
     parameters {
        string( defaultValue: "",name: 'buildnum')
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
                    //final String url = "https://jfrgfreetst.jfrog.io/artifactory/api/storage/example-repo-local/?sort"

                   

                  print("the folder path is:"+' '+folder_path+" and image is: "+image_name)
                   //print(Path)
                }
            }
        }
    }
}
def curlmethod(String url, String JFROG_ID,String bn ) {

 String lt
    if(bn > 1){
        lt = sh(script: "curl -u $JFROG_ID -s $url | grep uri |awk '{print \$3}'| sed 's+\"++g' | sed 's+/++g' | sed 's+,++g' |sed 's+'https:jfrgfreetst.jfrog.ioartifactoryapistorageexample-repo-local'++g' | sed 's+'Mypath2'++' |head -c -2 | head -$bn | tail -1", returnStdout: true).trim();
    }else{
        lt = sh(script: "curl -u $JFROG_ID -s $url | grep uri |awk '{print \$3}'| sed 's+\"++g' | sed 's+/++g' | sed 's+,++g' |sed 's+'https:jfrgfreetst.jfrog.ioartifactoryapistorageexample-repo-local'++g' | sed 's+'Mypath2'++' |head -c -2 | head -$bn", returnStdout: true).trim();
    }
    
    return lt

}
def curlmethodnew(String Path, String JFROG_ID ) {

String resp = sh(script: "curl -u $JFROG_ID -s $Path | jq -r '.children[].uri' | sed 's+\"++g' | sed 's+/++g' | sed 's+,++g' | sort -V | tail -1", returnStdout: true).trim()

return resp
 
}

