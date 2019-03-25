node{
   stage('SCM Checkout'){
     git 'https://github.com/vimalprasathr/helloworld-java-mvn.git'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'Maven', type: 'maven'   
      sh "/var/jenkins_home/tools/hudson.tasks.Maven_MavenInstallation/Maven/bin/mvn -f pom.xml clean install package"
   }
   stage('Deploy to Tomcat'){
      
      sshPublisher(publishers: [sshPublisherDesc(configName: '192.168.2.36', sshCredentials: [encryptedPassphrase: '{AQAAABAAAAAQDYOTL1ApjBBsaSUrlnLnHo0MAxtugGV5QLVMdLn+4TQ=}', key: '', keyPath: '', username: 'root'], transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: 'target', sourceFiles: '**/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
   }
   
    stage('Email Notification'){
      mail bcc: '', body: '''Hi Welcome to jenkins email alerts build has been completed
      Thanks
      Vimal''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'vprasath27@gmail.com'
   }
  
}
