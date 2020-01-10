pipeline
{
		agent any
		stages
		{
		stage ('MuleSoft Open Banking API - Build Application (Build)')
		{
			steps
			{
			bat 'mvn clean install -DskipTests'
			}
		}
		
		stage ('MuleSoft Open Banking API - Deploy To Nexus (Code Artifactory)')
		{	
			steps
			{
			bat 'mvn install deploy -DskipTests -s C:\\Users\\DELL\\.m2\\settings.xml'
			}
		}
		
		stage ('MuleSoft Open Banking API - Deploy To AnyPoint CloudHub Sandbox (Deploy)')
		{
			steps
			{
			bat 'mvn package deploy -DmuleDeploy -DskipTests -s C:\\Users\\DELL\\.m2\\settings.xml'
			}
		}		

		stage ('MuleSoft Open Banking API - Newman Test (Integration & Regression Testing)')
		{
			steps
			{
			bat 'C:\\Users\\DELL\\AppData\\Roaming\\npm\\newman run E:\\Mumbai-Mule-Meetup\\OpenBanking_Accounts_API_Collection.postman_collection.json -r htmlextra --reporter-htmlextra-export E:\\Mumbai-Mule-Meetup'
			}
		}
		}

}