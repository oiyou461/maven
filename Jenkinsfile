pipeline {
    agent any
    environment {
            // 设置你的 Git 仓库地址和 SSH 密钥的路径
            GIT_REPO = 'git@github.com:oiyou461/maven.git'
            SSH_PRIVATE_KEY = credentials('ssh-key-id') // Jenkins 密钥 ID
    }
    stages {
        stage('Checkout Code') {
                    steps {
                        // 使用 SSH 拉取代码
                        script {
                            // 配置 SSH 密钥用于 Git 拉取
                            sh '''
                            mkdir -p ~/.ssh
                            echo "$SSH_PRIVATE_KEY" > ~/.ssh/id_rsa
                            chmod 600 ~/.ssh/id_rsa
                            # 禁用 SSH 主机验证
                            echo "StrictHostKeyChecking no" >> ~/.ssh/config
                            '''
                            // 拉取代码
                            sh 'git clone $GIT_REPO'
                        }
                    }
                }
    }

}