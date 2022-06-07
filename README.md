### Simulacion
## 4.1 Paquete Simple PDU
1) 32 bits
2) 190.190.1.2
3) 7.7.0.2
4) 
In Layers:
	Layer 1: 
				1. FastEthernet0 receives the frame.
	Layer 2: 
				1. The frame's destination MAC address matches the receiving port's MAC address, the broadcast address, or a multicast address.
				2. The device decapsulates the PDU from the Ethernet frame.
	Layer 3:
				1. The packet's destination IP address matches the device's IP address or the broadcast address. The device de-encapsulates the packet.
				2. The packet is an ICMP packet. The ICMP process processes it.
				3. The ICMP process received an Echo Request message.
Out Layers: 
	Layer 1: 
				1. The ICMP process replies to the Echo Request by setting ICMP type to Echo Reply.
				2. The ICMP process sends an Echo Reply.
				3. The destination IP address 190.190.1.2 is not in the same subnet and is not the broadcast address.
				4. The default gateway is set. The device sets the next-hop to default gateway.
	Layer 2:
				1. The next-hop IP address is a unicast. The ARP process looks it up in the ARP table.
				2. The next-hop IP address is in the ARP table. The ARP process sets the frame's destination MAC address to the one found in the table.
				3. The device encapsulates the PDU into an Ethernet frame.
	Layer 3:
				1. FastEthernet0 sends out the frame.



## 4.2 Mas Paquetes
1) 32 bytes
2) Primero se envia un paquete de tipo DNS, el cual se mueve hasta el servidor DNS y de vuelta a quien hizo la request para averiguar cual es la IP a la que se resuelve el hostname (www.dinseyplus.com).
	Luego, aparece un paquete de tipo TCP, el cual se encarga de navegar hasta la IP que resolvio la DNS, el cual al llegar a su destino, vuelve al origen.
	Finalmente, cuando el paquete TCP vuelve al laptop, se envia un paquete HTTP el cual pide la informacion del html de la pagina. Este proceso se repite hasta cargar la pagina completa.
3) Paquete DNS pasa por:
							0. Laptop
							1. Home Router Manolito
							2. Router Gateway Manolito
							3. Router central
							4. Router DNS
							5. Server DNS
							6. Router DNS
							7. Router central
							8. Router Gateway manolito
							9. Home Router Manolito
							10. Laptop 
 Paquete TCP pasa por:
							0. Laptop
							1. Home Router Manolito
							1.1 PC
							1.2 Celular
							2. Router Gateway Manolito
							3. Router central
							4. Router Disney+
							5. Server Disney+
							6. Router Disney+
							7. Router central
							8. Router Gateway manolito
							9. Home Router Manolito
							10. Laptop 
 Paquete TCP pasa por:
							0. Laptop
							1. Home Router Manolito
							1.1 PC
							1.2 Celular
							2. Router Gateway Manolito
							3. Router central
							4. Router Disney+
							5. Server Disney+
							6. Router Disney+
							7. Router central
							8. Router Gateway manolito
							9. Home Router Manolito
							10. Laptop 
Notar que luego de pasar por el Home Router, el paquete pasa por todos los demas dispositivos, aunque se resuelve que la IP del dispositivo es diferente al destino por lo tanto el paquete muere ahi.