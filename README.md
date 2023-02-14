# LAB 05 - Interconectividad entre redes

Enero 16 de 2023*, Ramón Peinado Ruiz

Vamos a aprender a usar las interconectividad entre redes.

**Objetivos:**

------

• Task 1: Aprovisionar el entorno de laboratorio. 

• Task 2: Configurar el emparejamiento de redes virtuales locales y globales.

• Task 3: Probar la conectividad entre sitios.

**Diagrama:**

------

<img src="/img/1ºimagenn.png" alt="1ºimagenn" style="zoom:80%;" />

### TASK 1:

------

Vamos a desplegar 3 maquinas virtuales, cada una en una red virtual independiente, dos de ellas estaran en la misma region, la tercera se encontrara en otra region.



Creamos las maquinas mediante nuestras plantillas, subimos el archivo correspondiente al lab05 al CloudShell

<img src="/img/2ºimagenn.png" alt="2ºimagenn" style="zoom:80%;" />

Confirmamos que esten dentro del shell haciendo ls;

<img src="/img/3ºimagenn.png" alt="3ºimagenn" style="zoom:80%;" />

Una vez confirmado, creamos las variables para asociar las dos distintas regiones, y el nombre del grupo de recursos, creamos el grupo y realizamos el despliegue mediante nuestras templates indicándole que lo queremos en dos localizaciones distintas

<img src="/img/4ºimagenn.png" alt="4ºimagenn" style="zoom:80%;" />

El grupo de recursos quedaría tal que asi:

<img src="/img/5ºimagenn.png" alt="5ºimagenn" style="zoom:100%;" />

### TASK 2:

------

Vamos a configurar el emparejamiento de redes virtuales locales y globales



Accedemos a la **az104-05-vnet0 > Emparejamiento(Peering) >Add**

<img src="/img/6ºimagenn.png" alt="5ºimagenn" style="zoom:100%;" />

| Settings                                                     | Value                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| This virtual network: Peering link name                      | **az104-05-vnet0_to_az104-05-vnet1**                         |
| This virtual network: Traffic to remote virtual network      | **Allow (default)**                                          |
| This virtual network: Traffic forwarded from remote virtual network | **Block traffic that originates from outside this virtual network** |
| Virtual network gateway                                      | **None**                                                     |
| Remote virtual network: Peering link name                    | **az104-05-vnet1_to_az104-05-vnet0**                         |
| Virtual network deployment model                             | **Resource manager**                                         |
| I know my resource ID                                        | unselected                                                   |
| Subscription                                                 | the name of the Azure subscription you are using in this lab |
| Virtual network                                              | **az104-05-vnet1**                                           |
| Traffic to remote virtual network                            | **Allow (default)**                                          |
| Traffic forwarded from remote virtual network                | **Block traffic that originates from outside this virtual network** |
| Virtual network gateway                                      | ** None**                                                    |

Mediante Cloud Shell seria asi:

<img src="/img/7ºimagenn.png" alt="7ºimagenn" style="zoom:100%;" />

Este peering es desde la vnet0<----->vnet1

------

Hay que hacer el de la vnet0<----->vnet2

| Settings                                                     | Value                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| This virtual network: Peering link name                      | **az104-05-vnet0_to_az104-05-vnet2**                         |
| This virtual network: Traffic to remote virtual network      | **Allow (default)**                                          |
| This virtual network: Traffic forwarded from remote virtual network | **Block traffic that originates from outside this virtual network** |
| Virtual network gateway                                      | **None**                                                     |
| Remote virtual network: Peering link name                    | **az104-05-vnet2_to_az104-05-vnet0**                         |
| Virtual network deployment model                             | **Resource manager**                                         |
| I know my resource ID                                        | unselected                                                   |
| Subscription                                                 | the name of the Azure subscription you are using in this lab |
| Virtual network                                              | **az104-05-vnet2**                                           |
| Traffic to remote virtual network                            | **Allow (default)**                                          |
| Traffic forwarded from remote virtual network                | **Block traffic that originates from outside this virtual network** |
| Virtual network gateway                                      | ** None**                                                    |

Con cloud shell seria asi:

<img src="/img/8ºimagenn.png" alt="7ºimagenn" style="zoom:100%;" />

------

***Y el de la vnet1<----->vnet2***

| Settings                                                     | Value                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| This virtual network: Peering link name                      | **az104-05-vnet1_to_az104-05-vnet2**                         |
| This virtual network: Traffic to remote virtual network      | **Allow (default)**                                          |
| This virtual network: Traffic forwarded from remote virtual network | **Block traffic that originates from outside this virtual network** |
| Virtual network gateway                                      | **None**                                                     |
| Remote virtual network: Peering link name                    | **az104-05-vnet2_to_az104-05-vnet1**                         |
| Virtual network deployment model                             | **Resource manager**                                         |
| I know my resource ID                                        | unselected                                                   |
| Subscription                                                 | the name of the Azure subscription you are using in this lab |
| Virtual network                                              | **az104-05-vnet2**                                           |
| Traffic to remote virtual network                            | **Allow (default)**                                          |
| Traffic forwarded from remote virtual network                | **Block traffic that originates from outside this virtual network** |
| Virtual network gateway                                      | **None**                                                     |

Con Cloud Shell seria así:

<img src="/img/9ºimagenn.png" alt="7ºimagenn" style="zoom:100%;" />



Probamos la interconectividad mediante los siguientes comandos entre las distintas maquinas:

<img src="/img/10ºimagenn.png" alt="10ºimagenn" style="zoom:100%;" />

<img src="/img/11ºimagenn.png" alt="11ºimagenn" style="zoom:100%;" />



