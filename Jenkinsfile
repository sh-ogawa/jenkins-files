node {
   stage('update') {
      git([url: 'https://github.com/sh-ogawa/auto-test-demo.git', branch: 'sonar'])
   }
   stage('test') {
      bat 'mvn clean jacoco:prepare-agent test jacoco:report -e | echo "ignore failure"'
   }
   stage('analyze') {
      bat 'mvn sonar:sonar -e'
   }
}
