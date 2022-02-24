pipeline
{
agent any 
tools
{
// insatall the maven version configured as "m3" and add it to the path.
jdk 'Java 8'
maven "Maven 3.3.9"
}

stages 
{
stage('checkout')
{
steps
{
// get some code from a github repository
git url: 'https://github.com/kosurumuniraja/achu.git'
}
}
  stage('compile and build')
{
    steps {
        sh '''
        mvn clean install -U -Dmaven.test.skip=true
        '''
        
    }
}
}
}
