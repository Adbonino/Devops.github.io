# Creación de una máquina virtual


```
virt-install 
    --connect 
    qemu:///system 
    --network bridge:virbr0 
    --name EMS02 
    --ram 16384 
    --vcpu 8 
    --disk path=/var/opt/opwv/logs/media/work/kvm/EMS02-os.qcow2,format=qcow2,bus=virtio,size=50 
    --location=/var/lib/libvirt/images/rhel-8.6-x86_64-dvd.iso 
    --extra-args="console=tty0 console=ttyS0,115200" 
    --graphics none 
    --check all=off
```

## Servicio para poder ingresar por consola desde el HOST. - consola serie virtual

```
# systemctl enable serial-getty@ttyS0.service 
# systemctl start serial-getty@ttyS0.service 
```
Luego desde el Host puedo ingresar a la console del invitado con el siguiente comnado:
```
# virsh console VM_NAME
Connected to domain VM_NAME 
Escape character is ^] 
```
Presione ENTER para acceder al login.
Para salir de la consola virtual presionar CTRL +]

# Clonar un maquina
virt-clone --original EMS01 --name ORCHvLB01 --file /var/opt/opwv/logs/media/work/kvm/ORCHvLB01-os.qcow2
  283  virsh EMS01 stop
  284  virsh shutdown EMS01
  285  virsh list --all
  286  virt-clone --original EMS01 --name ORCHvLB01 --file /var/opt/opwv/logs/media/work/kvm/ORCHvLB01-os.qcow2
  287  virsh list --all
  288  virt-clone --original EMS01 --name FWDvLB01 --file /var/opt/opwv/logs/media/work/kvm/FWDvLB01-os.qcow2




Detener una máquina virtual
```
# virsh shutdown VM_NAME
```
