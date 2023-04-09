To connect to vCenter ue the following:
  - Connect-VIServer -Server vcenter.kazmi.lab -User Administrator@vsphere.local -Password SUPER-PASS
To created new:
  - New-VM -Template TEMPLATE_NAME -Name VM-NAME -Datastore DATASTORE -DiskStorageFormat Thin -Location FOLDER -NetworkName vSwitch -VMHost esxi.lab.local
  - Get-vm VM_NAME | Get-NetworkAdapter | Set-NetworkAdapter -MacAddress 00:50:56:xx:xx:xx
