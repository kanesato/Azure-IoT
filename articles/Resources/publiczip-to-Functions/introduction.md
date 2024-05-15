[Back to the demo's homepage](../../IoTDigitalTwinDemo.md#-azure-functions-)

## How to create the functions' zip files


1. ### Download the SampleFunctionsApp folder from the link below.
https://learn.microsoft.com/ja-jp/samples/azure-samples/digital-twins-samples/digital-twins-samples/

2. ### Copy the SampleFunctionsApp folder to a Windows machine.
3. ### Run the command "dotnet publish -c Release" in the folder. (Need .Net SDK)
4. ### Two new folders will be deployed (bin and obj). 
5. ### Run the command below on powershell to compress the applications in a zip file named "publish.zip".
    - ※or you can use the zip file below<br>
publish.zip(./publiczip-to-Functions/publish.zip)

```bash
Compress-Archive -Path C:\digital-twins-samples-main\AdtSampleApp\SampleFunctionsApp\bin\Release\net7.0\publish\* -DestinationPath .\publish.zip
```
    
6. ### Run the command below on powershell to upload the zip file to Azure Functions.

    - Upload program file to the Azure function
```bash
az functionapp deployment source config-zip --resource-group < resource group name > --name <Azure Functions Name > --src <full path of the publish.zip>
```
[reference]:Deploy by using Azure CLI<br>
(https://learn.microsoft.com/en-us/azure/azure-functions/deployment-zip-push#cli)


### e.g.
```bash
az functionapp deployment source config-zip --resource-group "adt-demo" --name "adt-demo" --src "/Volumes/ExtraDisk/Github/AzureDoc/TechTips/articles/IoTRef/publiczip-to-Functions/publish.zip"
```



