# Convert fixed to thin provisioned volumes on Azure Stack HCI

Lo primero que haremos sera validar el estado de los Storage:

bash```
Get-VirtualDisk |
Select FriendlyName, ProvisioningType, ResiliencySettingName,
       HealthStatus, OperationalStatus,
       @{N="SizeTB";E={:Round($_.Size/1TB,2)}},
       @{N="AllocatedTB";E={:Round($_.AllocatedSize/1TB,2)}} |
Format-Table -AutoSize
```
