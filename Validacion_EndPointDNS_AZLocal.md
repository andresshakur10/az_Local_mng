Validacion de EndPoint DNS de Azure Local
```bash
Resolve-DnsName mcr.microsoft.com; Test-NetConnection mcr.microsoft.com -Port 443
```

#Validar multiples EndPoint.
Cómo interpretar el resultado

mcr.microsoft.com             | DNS: OK | TCP443: True ✅
azureedge.net                 | DNS: FAIL | TCP443: FAIL ❌
blob.core.windows.net        | DNS: FAIL | TCP443: FAIL ❌

PATRÓN QUE DEBES BUSCAR
DNS: FAIL
TCP443: FAIL

👉 problema = DNS / Firewall
DNS: OK
TCP443: False

👉 problema = firewall / proxy

```bash
$endpoints="mcr.microsoft.com","westus.data.mcr.microsoft.com","northeurope.data.mcr.microsoft.com","westeurope.data.mcr.microsoft.com","azurearcfork8s.azurecr.io","linuxgeneva-microsoft.azurecr.io","azurearcfork8sdev.azurecr.io","hybridaks.azurecr.io","aszk8snetworking.azurecr.io","dl.delivery.mp.microsoft.com","do.dsp.mp.microsoft.com","prod.do.dsp.mp.microsoft.com","eastus.dp.kubernetesconfiguration.azure.com","sts.windows.net","ecpacr.azurecr.io","raw.githubusercontent.com","msk8s.api.cdp.microsoft.com","msk8s.sb.tlu.dl.delivery.mp.microsoft.com","time.windows.com","k8connecthelm.azureedge.net","kvamanagementoperator.azurecr.io","packages.microsoft.com","k8sconnectcsp.azureedge.net","prod.hot.ingest.monitor.core.windows.net","prod5.prod.hot.ingestion.msftcloudes.com","eastus.dp.prod.appliances.azure.com","download.microsoft.com","pas.windows.net","guestnotificationservice.azure.com","his.arc.azure.com","guestconfiguration.azure.com","servicebus.windows.net","waconazure.com","login.microsoftonline.com","graph.windows.net","graph.microsoft.com","login.windows.net","portal.azure.com","blob.core.windows.net","management.azure.com","azurestackhci.azurefd.net","go.microsoft.com","azureedge.net"; foreach($e in $endpoints){try{$dns=Resolve-DnsName $e -ErrorAction Stop; $tcp=(Test-NetConnection $e -Port 443 -WarningAction SilentlyContinue).TcpTestSucceeded; "$e | DNS: OK | TCP443: $tcp"}catch{"$e | DNS: FAIL | TCP443: FAIL"}}
```
