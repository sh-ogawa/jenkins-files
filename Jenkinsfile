node {
   stage('update') {
      git([url: 'https://github.com/sh-ogawa/auto-test-demo.git', branch: 'sonar'])
   }
   stage('test') {
      sh 'mvn clean jacoco:prepare-agent test jacoco:report -e | echo "ignore failure"'
   }
   stage('analyze') {
      sh 'mvn sonar:sonar -e |echo "ignore failure"'
   }
   stage('Xray scan')
      {
        def xrayConfig = [
          //Mandatory parameters
          'buildName'         : env.JOB_NAME,
          'buildNumber'       : '3',

          //Optional
          'failBuild'        :false //Default
        ]

        // Scan xray build
        def xrayResults = artServer.xrayScan xrayConfig
        // Print full report from xray
        echo xrayResults as String
      }
}
