# Export Cost data

## Data older than 1 year can't be exported using Azure portal 'Cost Export'. In that case below script to be executed in Azure cloud Shell and export FinOps Cost data for a speific data range. 

**Note:** Below script exports data for FinOps hub. It is not for generic data export to a storage account. 

```
start -finOpsCostExport -Name $name
- scope $scope
- StartDate 2020-01-01
- EndDate 2025-01-31


start -finOpsCostExport -Name <name of the cost export>
- scope "/subscriptions/000000-0000-000-00000000"
- StartDate 2020-01-01
- EndDate 2025-01-31

```
