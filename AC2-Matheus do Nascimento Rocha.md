# O que é endereço IP
Um endereço IP é um endereço usado para identificar de maneira única um dispositivo em uma rede IP. O endereço é composto de 32 bits binários, que podem ser divisíveis em uma porção de rede e de host com a ajuda de uma máscara de sub-rede. Os 32 bits binários estão divididos em quatro octetos (1 octeto = 8 bits). Cada octeto é convertido em decimal e separado por um ponto final (ponto). Por esse motivo, um endereço IP deve ser expressado no formato decimal pontuado (por exemplo, 172.16.81.100). O valor em cada octeto varia de 0 a 255 decimais ou de 00000000 a 11111111 binários.

## Informações adicionais
1. **Máscara de subrede**
Uma combinação de 32 bits usada para descrever qual parte de um endereço refere-se à sub-rede e qual parte refere-se ao host.
2. **Sub-Rede**
 _Uma parte de uma rede que compartilha um determinado endereço de sub-rede._
3. **Endereço**
~~A identificação numérica exclusiva atribuída a um host ou uma interface em uma rede.~~
4. **Interface**
**_Uma conexão de rede._**

## Classes de rede
Há cinco classes diferentes de redes, de A a E:
|Classe|Inicio|Fim|CIDR|OBS|
|:-:|:---------:|:----------------:|:--:|:-------:|
| A | 1.0.0.1 | 126.255.255.254 | /8 | / |
| B | 128.0.0.1 | 191.255.255.254 | /16 | / |
| C | 192.0.0.1 | 223.255.255.254 | /24 | / |
| D | 224.0.0.0 | 239.255.255.255 |   | Multicast |
| E | 240.0.0.0 | 247.255.255.255 |   | Reservado pela IETF  |

> Para mais informações sobre o IETF, [clique aqui](https://www.ietf.org/).

### Figura 1
![image](https://user-images.githubusercontent.com/26606376/93838468-25d50980-fc60-11ea-8929-1b1086ff2fbd.png)

Vamos tratar somente das classes:
* A
* B
* C

Em um endereço de Classe A, como o primeiro octeto é a porção da rede, o exemplo da Classe A na Figura 1 tem um endereço de rede principal de 1.0.0.0 a 127.255.255.255. Os octetos 2, 3 e 4 (os 24 bits seguintes) são para o gerente de rede dividir em sub-redes e hosts quando possível. Os endereços da Classe A são utilizados em redes que têm mais de 65.536 hosts (na verdade, até 16777214 hosts!).

Em um endereço de Classe B, como os dois primeiros octetos são a porção da rede, o exemplo da Classe B na Figura 1 tem um endereço de rede principal de 128.0.0.0 a 191.255.255.255. Os octetos 3 e 4 (16 bits) são para sub-redes local e hosts. Os endereços da Classe B são usados em redes que tenham entre 256 e 65534 hosts.

Em um endereço da Classe C, os primeiros três octetos são a porção da rede. O exemplo da Classe C na Figura 1 tem um endereço de rede importante de 192.0.0.0 - 223.255.255.255. O Octeto 4 (8 bits) é para sub-redes local e hosts - perfeito para redes com menos de 254 hosts.

Para finalizarmos, aqui vai um script para windows onde conseguimos renovar o endereço IP e mais umas coisinhas. :blush: :blush:

~~~BAT
echo off
@color 0a
@title Renovando IP
cls
echo.
echo.
echo Agora vamos comecar o processo para renovar seu endereco ip?
pause
echo Escolha uma opcao
echo (1) Renovar IP e Resetar interface de rede
echo (2) Renovar IP
echo (3) Resetar Interface de rede
echo (4) Sair
set /p resp=
if "%resp%" == "1" (goto process) else (goto end)
echo.
:process
ipconfig /flushdns
ipconfig /registerdns
ipconfig /release
ipconfig /release6
ipconfig /renew
ipconfig /renew6
pause
netsh int ip reset resetlog.txt
netsh winsock show catalog
netsh winsock reset
echo.
echo IP renovado.
echo.
pause
echo Deseja Reiniciar o Computador?
echo (1) Sim
echo (2) Nao
set /p quest=
if "%quest%" == "1" (goto process) else (goto end)
:process
shutdown -r
pause
exit
if "%resp%" == "2" (goto process) else (goto end)
echo.
:process
ipconfig /flushdns
ipconfig /registerdns
ipconfig /release
ipconfig /release6
ipconfig /renew
ipconfig /renew6
echo.
echo IP renovado.
echo.
pause
exit
if "%resp%" == "3" (goto process) else (goto end)
echo.
:process
netsh int ip reset resetlog.txt
netsh winsock show catalog
netsh winsock reset
echo.
echo IP renovado.
echo.
pause
echo Deseja Reiniciar o Computador?
echo (1) Sim
echo (2) Nao
set /p quest=
if "%quest%" == "1" (goto process) else (goto end)
:process
shutdown -r
pause
exit
:end
pause
cls
exit
~~~

Professor me da 10 :raised_hands: :raised_hands: :raised_hands: 

#### Matheus merece um 10 ?

- [x] Sim
- [x] SIM
- [x] S I M
- [x] YES
- [x] NAI
- [x] Evet

@leonardobontempo @srperseu https://github.com/leonardobontempo/Aula3-DevOps/issues/18

\## TODO MATERIAL AQUI FOI ENCONTRADO NA INTERNET ##