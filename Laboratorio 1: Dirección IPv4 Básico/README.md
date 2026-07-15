Actividades
Configurar IPs.
Configurar Gateway.
Verificar ping.
Verificar ARP.
Verificar tabla de rutas.

#solucion
# Configuración del Router MikroTik

## Paso 1: Cambiar el nombre del router
/system identity set name=R1

## Paso 2: Configurar la interfaz hacia la Red 1 (PC1)
/ip address
add address=192.168.10.1/24 interface=ether1 comment="Red 1 - PC1"


## Paso 3: Configurar la interfaz hacia la Red 2 (PC2)
/ip address
add address=192.168.20.1/24 interface=ether2 comment="Red 2 - PC2"

## Paso 4: Verificar las direcciones IP configuradas
/ip address print


## Paso 5: Verificar el estado de las interfaces
/ interface print

## Paso 6: Verificar la tabla de rutas
/ip route print

## Paso 7: Verificar la tabla ARP
/ip arp print

## Paso 8: Probar la conectividad desde el router

### Ping hacia PC1
ping 192.168.10.10

### Ping hacia PC2
ping 192.168.20.10

# Configuración de las PCs (VPCS)

## PC1
ip 192.168.10.10/24 192.168.10.1
save

## PC2
ip 192.168.20.10/24 192.168.20.1
save

# Pruebas de conectividad

## Desde PC1
ping 192.168.10.1
ping 192.168.20.1
ping 192.168.20.10

## Desde PC2
ping 192.168.10.10
