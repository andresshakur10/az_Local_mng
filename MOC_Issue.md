# Resolutor de problemas en el MOC

- Cuando el moc tiene problemas se debe realizar los siguientes pasos:
1. Debe instalar el módulo ejecutando el siguiente comando en PowerShell como administrador en uno de los nodos:
   
```bash
Install-PackageProvider NuGet -Force

Install-Module PrivateCloud.DiagnosticInfo -Force

Import-Module PrivateCloud.DiagnosticInfo -Force

Install-Module -Name MSFT.Network.Diag
```

- Debes recopilar los datos del SDDC de uno de los nodos con el siguiente comando.
```bash
Get-SDDCDiagnosticInfo
```

- Ejecutar estos comandos de instalacion:
  
```bash
Install-Module Support.AksArc

Import-Module Support.AksArc

Test-SupportAksArcKnownIssues
```
- si se produce algún error:

```bash
Invoke-SupportAksArcRemediation
```
