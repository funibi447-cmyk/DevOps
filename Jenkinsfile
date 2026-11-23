pipeline {
    agent any
    stages {
        stage('Подготовка окружения') {
            steps {
                script {
                    dir('ansible_lr3') {
                        ansiblePlaybook(
                            playbook: 'firstPlaybook.yml',
                            inventory: 'inventory/stend1/hosts',
                            tags: 'install_docker'
                        )
                        ansiblePlaybook(
                            playbook: 'firstPlaybook.yml',
                            inventory: 'inventory/stend1/hosts',
                            tags: 'clone_repos'
                        )
                    }
                }
            }
        }
        stage('Запуск приложений') {
            steps {
                script {
                    dir('ansible_lr3') {
                        ansiblePlaybook(
                            playbook: 'firstPlaybook.yml',
                            inventory: 'inventory/stend1/hosts',
                            tags: 'start_services'
                        )
                    }
                }
            }
        }
    }
}
