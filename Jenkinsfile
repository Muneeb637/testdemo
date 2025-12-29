pipeline {
agent any
stages {
stage('Use Secret Securely') {
steps {
withCredentials([string(credentialsId: 'user_secret_key', variable: 'MYSECRET')]) {
echo "The secret value is: $MYSECRET"
// In real life you would use it in curl, docker login, etc.
}
}
}
}
}
