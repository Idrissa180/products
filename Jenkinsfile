node{

    stage("SCM Checkout"){
        git credentialsId: 'git-credential', url: 'https://github.com/idrissa180/products.git'
    }

    stage("Build Docker Image"){
        sh "docker build -t enoch180/produits:1.0 ."
    }
    
}
