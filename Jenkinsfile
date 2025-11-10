pipeline {
    agent any

    stages { // <--- 1-ша ВІДКРИТА
        
        stage('Build') { // <--- 2-га ВІДКРИТА
            steps { // <--- 3-тя ВІДКРИТА
                // Ваша команда 'bat' з /restore
                bat 'call "C:\\Program Files (x86)\\Microsoft Visual Studio\\2022\\BuildTools\\MSBuild\\Current\\Bin\\MSBuild.exe" test_repos.sln /restore /t:Build /p:Configuration=Debug /p:Platform=x64'
            } // <--- 3-тя ЗАКРИТА
        } // <--- 2-га ЗАКРИТА

        stage('Test') { // <--- 4-та ВІДКРИТА
            steps { // <--- 5-та ВІДКРИТА
                bat 'call x64\\Debug\\test_repos.exe --gtest_output=xml:test_report.xml'
            } // <--- 5-та ЗАКРИТА
        } // <--- 4-та ЗАКРИТА

    } // <--- 1-ша ЗАКРИТА (можливо, її і не вистачає)

    post { // <--- 6-та ВІДКРИТА
        always { // <--- 7-ма ВІДКРИТА
            junit 'test_report.xml'
        } // <--- 7-ма ЗАКРИТА
    } // <--- 6-та ЗАКРИТА

} // <--- ОСНОВНА ЗАКРИТА (або, можливо, не вистачає цієї)