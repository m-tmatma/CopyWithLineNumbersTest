pipeline  {
	def nuget = "C:\Program Files (x86)\NuGet\nuget.exe"

	agent any
	stages {
		stage('Checkout') {
			steps {
				checkout scm
			}
		}

		stage('Build') {
			steps {
				bat ('"${nuget}" restore CopyWithLineNumbers.sln')
				bat ("\"${tool 'MSBuild'}\" CopyWithLineNumbers.sln /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}")
			}
		}
		
		stage('Archive') {
			steps {
				archive ('CopyWithLineNumbers/bin/Release/CopyWithLineNumbers.dll')
				archive ('CopyWithLineNumbers/bin/Release/CopyWithLineNumbers.vsix')
				archive ('CopyWithLineNumbers/obj/Release/CopyWithLineNumbers.pdb')
			}
		}
	}
}
