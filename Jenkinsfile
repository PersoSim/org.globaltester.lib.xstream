node {
   stage 'Checkout'
   checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'org.globaltester.lib.xstream']], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'ccaa54ad-8940-4687-aebf-64979d3094fb', url: 'git@git.globaltester.org:org.globaltester.lib.xstream']]])
   checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'org.globaltester.parent']], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'ccaa54ad-8940-4687-aebf-64979d3094fb', url: 'git@git.globaltester.org:org.globaltester.parent']]])

   // Get the maven tool.
   // ** NOTE: This 'M3' maven tool must be configured
   // **       in the global configuration.           
   
   // Mark the code build 'stage'....
   stage 'Build'
   def mvnHome = tool 'M305'

   // Run the maven build
   sh "cd org.globaltester.lib.xstream/org.globaltester.lib.xstream/ && ${mvnHome}/bin/mvn -Dmaven.test.failure.ignore clean package"

}
