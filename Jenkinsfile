node
{
	try
	{
		stage ('MuleSoft Open Banking API - Build Application (Build)')
		{
			bat 'mvn clean install -DskipTests'
		}
		
		stage ('MuleSoft Open Banking API - Unit Testing (MUnit)')
		{
			bat 'mvn test'
		}
		
		stage ('MuleSoft Open Banking API - Deploy To Nexus (Code Artifactory)')
		{
			bat 'mvn install deploy -DskipTests -s C:\\Users\\DELL\\.m2\\settings.xml'
		}
		
		stage ('MuleSoft Open Banking API - Deploy To AnyPoint CloudHub Sandbox (Deploy)')
		{
			bat 'mvn package deploy -DmuleDeploy -DskipTests -s C:\\Users\\DELL\\.m2\\settings.xml'
		}		

		stage ('MuleSoft Open Banking API - Newman Test (Integration & Regression Testing)')
		{
			bat 'C:\\Users\\DELL\\AppData\\Roaming\\npm\\newman run E:\\Mumbai-Mule-Meetup\\OpenBanking_Accounts_API_Collection.postman_collection.json -r htmlextra --reporter-htmlextra-export E:\\Mumbai-Mule-Meetup'
		}
	}catch(err)
		{
			emailext body: '<b>Jenkins Job MuleSoft OpenBanking has been failed.</b><br><br>', 
			subject: 'MuleSoft OpenBanking Job Failed', 
			to: 'jitendra25555375@gmail.com'
		}
}