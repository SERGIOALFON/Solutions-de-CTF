# Solutions-de-CTF
**Machines Brocoli**


<img width="586" height="268" alt="image" src="https://github.com/user-attachments/assets/38a6a502-5624-4297-b4e9-832fb58fcb93" />



**Máquina:** Brócoli

**Plataforma:** Hackers Labs

**Dificultad:** Fácil – Intermedia (dependiendo tu experiencia)

**Categoría:** Web / Enumeración / Escalada de privilegios


**Fase 1: Reconocimiento**


En esta etapa se identifican los servicios expuestos en la máquina.


# Bash 

- nmap -sn < Ip >/24   

- nmap -sSCV -vvv -n -Pn --open --min-rate=5000 192.168.10.34   

<img width="658" height="298" alt="image" src="https://github.com/user-attachments/assets/75fda72b-ddfd-433b-828a-50fc6d7a8506" />




**Fase 2: Enumeración Web**


- Browser < IP >

- Codigo  // YXF1aW5vaGF5bmFkYSBwZWxvYnJvY29saQo=

  
# Bash

 echo 'YXF1aW5vaGF5bmFkYSBwZWxvYnJvY29saQo=' | base64 -d


 # Fuzzing Directorios

gobuster dir -u http://192.168.10.34/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php, txt, htlm

<img width="663" height="356" alt="image" src="https://github.com/user-attachments/assets/43ef64e8-6c0b-4a4b-aa49-dba8866f377c" />


- Browser < IP >/uploads/


<img width="500" height="249" alt="image" src="https://github.com/user-attachments/assets/8251d28e-baa8-4d5a-99c3-1ad3894c560f" />


- Click informebrocoli.txt

- MD5 913026c7754df0fbdc89b75007ad5a66

- Crackstations decifrar codigo (mecmec)


# Explotación

- Shell Inversa

  


