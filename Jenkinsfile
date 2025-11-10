pipeline {
    agent any

    stages {  // <-- Цей блок був пропущений
        stage('Build') {
            steps {
                // ВАЖЛИВО: Переконайтеся, що шлях правильний саме для ВАШОГО комп'ютера!
                // Ми використовуємо 'call' для стабільності запуску bat-файлів у Jenkins.
                bat 'call "C:\\Program Files (x86)\\Microsoft Visual Studio\\2022\\BuildTools\\MSBuild\\Current\\Bin\\MSBuild.exe" test_repos.sln /t:Build /p:Configuration=Debug /p:Platform=x64'
            }
        }

        stage('Test') {
            steps {
                // Запуск скомпільованого exe-файлу тестів.
                // 'call' також тут не завадить для надійності.
                bat 'call x64\\Debug\\test_repos.exe --gtest_output=xml:test_report.xml'
            }
        }
    }

    post {
        always {
            // Цей крок збере звіт про тестування (JUnit format), навіть якщо тести впадуть.
            junit 'test_report.xml'
        }
    }
}