# Resoluci-n-M-quina-Databreach

Primeramente iniciamos la maquina vulnerable

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 223906" src="https://github.com/user-attachments/assets/5655c97b-9624-42c7-9b2d-5d3d16c14d15" />

# Reconocimiento

Luego procedemos a hacer un escaneo de red utilizando la herramienta **Nmap**

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 223951" src="https://github.com/user-attachments/assets/9e57a63a-331f-4734-afda-597f9e8b6323" />

Como podemos observar tenemos los puertos **22, 80, 3306, 33060** 

Ingresamos a la dirección ip utilizando un buscador para verificar que información nos arroja y si nos es de importancia para seguir nuestro camino resolviendo esa maquina, y nos encontramos que es un login 

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 224728" src="https://github.com/user-attachments/assets/d3867d2d-b5c3-412f-9259-dc896e5901d1" />

Procedimos a hacer prueba utilizando codigo sql y obtuvimos acceso, encontramos información valiosa inyectando algunos comandos para visualizar base de datos y demas

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 225946" src="https://github.com/user-attachments/assets/69853dfb-2dc8-4282-8606-380408ea23e6" />
<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 225955" src="https://github.com/user-attachments/assets/4366b105-e65b-4c79-ae3c-b72df316e7b4" />
<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 230005" src="https://github.com/user-attachments/assets/faeeb0b8-b0d7-4d32-bac2-fcb74d1661a9" />
<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 230100" src="https://github.com/user-attachments/assets/1a4d2130-0319-4765-bf4b-a44cb3b808e7" />

Luego ingresamos el siguiente comando en busqueda de información y obtuvimos credenciales

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 230735" src="https://github.com/user-attachments/assets/e5c31563-d1f2-478b-9cec-88993ea87e00" />

Procedi a hacer intentar ingresar a la maquina ingresando las credenciales pero no tuve acceso

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 230923" src="https://github.com/user-attachments/assets/b82c4846-8e55-4198-b519-dbf3e6461fd8" />

## Explotación
Intente con nuestra herramienta amiga hydra y obtuvimos las credenciales para el usuario **john** asi que procedimos a ingresar a la maquina 

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 231348" src="https://github.com/user-attachments/assets/62ea5395-5947-47c2-a112-6c705cf1415b" />

Obtuvimos acceso

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 231413" src="https://github.com/user-attachments/assets/2d448384-ca63-4bc0-afe1-a1a7b86ef324" />

Una vez dentro de la maquina procedimos a listar los archivos pero no encontramos nada, asi que listamos los binarios en busqueda de alguno que nos sirviera para escalar privilegios

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 231548" src="https://github.com/user-attachments/assets/9054872c-2b74-4248-8795-7303b9066add" />

## Escalada de privilegios

Nos encontramos el binadio **chmod** el cual nos permite cambiar los permisos a los binarios o archivos, asi que procedimos a cambiar los permisos al binario /bin/bash, una vez cambiado los permisos procedimos a intentar abrirlo y walaa obtuvimos acceso como john

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 231801" src="https://github.com/user-attachments/assets/f85b0cfc-9dc2-4d1e-8ec3-d7ab4ed68918" />

Asi que luego procedimos a utilizar el comando /bin/bash con la bandera -p la cual crea persistencia y obtuvimos privilegios como **root**

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 232100" src="https://github.com/user-attachments/assets/4cc04691-daf8-432e-8d6a-cca4343859fb" />

## Resultados

Listamos los archivos, ingresamos a la carpeta **root**, volvimos a listar los archivos y encontramos el archivo flag.txt

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 232123" src="https://github.com/user-attachments/assets/aaf70b80-6ef0-4236-bdf7-f77b4457426c" />

Y de esta manera concluimos nuestra maquina

<img width="1920" height="1140" alt="Captura de pantalla 2026-03-17 232133" src="https://github.com/user-attachments/assets/58faff99-4629-4c47-8297-652d2422c339" />


