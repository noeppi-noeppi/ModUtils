#!/usr/bin/env groovy

pipeline {
    agent any
    tools {
        jdk 'java${jdk}'
    }
    environment { 
        MODGRADLE_CI = 'true'
    }
    stages {
        stage('Clean') {
            steps {
                echo 'Cleaning Project'
                sh 'chmod +x gradlew'
                sh './gradlew clean'
            }
        }

        stage('Build and Publish') {
            steps {
                echo 'Building'
                sh './gradlew build publish'
                /* sh './gradlew build curseforge modrinth publish' */
            }
        }

        stage('Archive artifacts') {
            steps {
                echo 'Archive'
                archiveArtifacts 'build/libs*/*.jar'
            }
        }
    }
}
