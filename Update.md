
- Se utiliza para ver en que version del OS y del systema de AZ Local.
```bash
Get-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion"
Get-StampInformation
```
- Consulta las actualizaciones diponibles o en proceso.
```bash
Get-SolutionUpdate | ft Version,State,UpdateStateProperties,HealthState
```

- Comando para validar el status de las actualizaciones.
```bash
Get-ActionPlanInstances | Select-Object ActionPlanName, status, StartDateTime, EndDateTime, InstanceID | Sort-Object EndDateTime | ft
```
