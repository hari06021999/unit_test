node {
    try {
        checkout scm

        stage('Preparation') {
           sh 'ceedling clean'
        }
        
        stage('Unit Test') {
            dir("can") {
                sh 'ceedling test:all'
                 // sh 'ceedling gcov:all'
                 // sh 'ceedling utils:gcov'
            }
        }
        stage('Coverage Test') {
            dir("can") {
                sh 'ceedling gcov:all'
            }
        }
        
        stage('Coverage XML Generate') {
            dir("can") {
                sh 'ceedling utils:gcov'
                // sh 'cat /var/lib/jenkins/workspace/CAN_TEST/can/build/artifacts/gcov/GcovCoverageResults.html'
              
            }
        }
        
    }
   
    catch (e) {
        throw e
    }
      finally{
           emailext to: "hariprithi99@gmail.com",
            subject: "Test Email From Jenkins",
            body: "Hey Buddy you got mail! <br>  BUILD STATUS: ${currentBuild.currentResult}: Job ${env.JOB_NAME}\nMore Info can be found here: ${env.BUILD_URL}",
            // attachLog: true,
            attachmentsPattern: "can/build/artifacts/gcov/*.html",attachLog: true
    }
}

// pipeline {
//     agent any 

//     environment {
//         TOOL_DIR = "${WORKSPACE}\\2W_Test\\src\\CICDTool"
//     }

//     stages {
//         stage('Build') { 
//             steps {
//                 bat "${TOOL_DIR}\\build.bat ${WORKSPACE}\\Debug Debug all"
//             }
//         }
        
    
       
//     }
//      post{
//         always{
//             emailext to: "hariprithi99@gmail.com",
//             subject: "Test Email From Jenkins",
//             body: "I Hope all of you getting Email's From Jenkins <br>  BUILD STATUS: ${currentBuild.currentResult}: Job ${env.JOB_NAME}\nMore Info can be found here: ${env.BUILD_URL}",
//             attachLog: true
//         }
//     }
     
   
       
// }
    
