1) Create Custom Quality Gate in SonarCloud and Add conditions to the Quality Gate
2) Assign this Quality Gate to the Project
3) Add script in azure-pipeline.yaml file to enable quality gate check (Note: This will fail your build in case Quality Gate fails)

sleep 5
sudo apt update
sudo apt install curl jq 
quality_status=$(curl -s -u 14ad4797c02810a818f21384add02744d3f9e34d: https://sonarcloud.io/api/qualitygates/project_status?projectKey=azuredevopsadodevsecopsprojectkey | jq -r '.projectStatus.status')
echo "SonarCloud Analysis Status is $quality_status"; 
if [[ $quality_status == "ERROR" ]] ; then exit 1;fi


-----------Sample JSON Response from SonarCloud or SonarQube Quality Gate API---------------------

{
	"projectStatus": {
		"status": "ERROR",
		"conditions": [
			{
				"status": "ERROR",
				"metricKey": "coverage",
				"comparator": "LT",
				"errorThreshold": "90",
				"actualValue": "0.0"
			}
		],
		"periods": [],
		"ignoredConditions": false
	}
}
