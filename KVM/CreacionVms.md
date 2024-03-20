# Creación de una máquina virtual


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


## Servicio para poder ingresar por consola desde el HOST.

systemctl enable serial-getty@ttyS0.service 

systemctl start serial-getty@ttyS0.service 
