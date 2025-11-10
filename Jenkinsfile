pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // ВАЖЛИВО: Перевірте, чи цей шлях до MSBuild правильний на ВАШОМУ комп'ютері!
                // Якщо не працює, знайдіть де у вас лежить MSBuild.exe і вставте сюди повний шлях.
                bat '"C:\\Program Files\\Microsoft Visual Studio\\2022\\Community\\MSBuild\\Current\\Bin\\MSBuild.exe" test_repos.sln /t:Build /p:Configuration=Debug /p:Platform=x64'
            }
        }

        stage('Test') {
            steps {
                // Запуск тестів. Переконайтеся, що шлях до exe файлу правильний відносно кореня репозиторію.
                bat "x64\\Debug\\test_repos.exe --gtest_output=xml:test_report.xml"
            }
        }
    }

    post {
        always {
            junit 'test_report.xml'
        }
    }
}