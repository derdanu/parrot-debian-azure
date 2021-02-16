# Parrot Security Linux custom install on Azure 

This is based on the work of https://nest.parrotsec.org/build/alternate-install with a few minor adjustments to fit this on Azure Debian 10 Marketplace image. 

## Create VM 
``` 
az group create -n myResourceGroup -l westeurop
az vm create -n myVm -g myResourceGroup --image debian --username parrot --password superSecure123#
``` 

## Run Extension (New or Existing VM) to deploy Parrot Security distribution
```
az vm extension set \
  --resource-group myResourceGroup \
  --vm-name myVM --name customScript \
  --publisher Microsoft.Azure.Extensions \
  --settings ./script-config.json
```