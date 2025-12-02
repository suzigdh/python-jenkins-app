pipeline {
    agent any
    
    environment {
        IMAGE_NAME = "python-print-app:latest"
    }
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/suzigdh/python-jenkins-app.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}")
                }
            }
        }
        
        stage('Run Container') {
            steps {
                script {
                    sh 'docker rm -f python-print-app || true'
                    sh 'docker run --name python-print-app ${IMAGE_NAME}'
                }
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline terminé avec succès !'
        }
        failure {
            echo 'Pipeline échoué.'
        }
    }
}


⚠️ **IMPORTANT** : Dans le Jenkinsfile, ligne 11, **remplacez `VOTRE-NOM`** par votre nom d'utilisateur GitHub !

4. Cliquez sur **"Commit new file"**

---

## **✅ Vérification finale**

Maintenant, votre repository `python-jenkins-app` devrait contenir **4 fichiers** :
```
python-jenkins-app/
├── README.md          (créé automatiquement)
├── app.py             (vous l'avez créé)
├── Dockerfile         (vous l'avez créé)
└── Jenkinsfile        (vous l'avez créé)
```

---

## **📦 C'est quoi un "repo" ?**

**"Repo"** = **"Repository"** = **Dépôt**

C'est simplement un **dossier de projet** sur GitHub qui contient tous vos fichiers.

**Analogie simple :**
- Repository = Un dossier sur votre ordinateur
- Fichiers = Les documents dans ce dossier

---

## **🚀 Utiliser ce repository dans Jenkins**

Maintenant que votre repo est créé :

### Sur Jenkins :

1. **"New Item"** → Nom : `PythonDockerPipeline`
2. Sélectionnez **"Pipeline"** → **OK**
3. Section **"Pipeline"** :
   - **Definition** : choisissez **"Pipeline script from SCM"**
   - **SCM** : **Git**
   - **Repository URL** : 
```
     https://github.com/suzigdh/python-jenkins-app.git
