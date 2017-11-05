pipeline  {
	stages {
		stage 'Checkout' {
			checkout scm
		}

		stage 'Build' {
			bat 'nuget restore CopyWithLineNumbers.sln'
			bat "\"${tool 'MSBuild'}\" CopyWithLineNumbers.sln /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"
		}
		
		stage 'Archive' {
			archive 'CopyWithLineNumbers/bin/Release/CopyWithLineNumbers.dll'
			archive 'CopyWithLineNumbers/bin/Release/CopyWithLineNumbers.vsix'
			archive 'CopyWithLineNumbers/obj/Release/CopyWithLineNumbers.pdb'
		}
	}
}
