![Image](https://github.com/user-attachments/assets/d4f8df59-f0ae-4b0e-82dc-33812a76861f)
# AUTO-PONTO
### _Um guia de acesso ao projeto NÃO FINALIZADO de automação de envio dos AFD gerados pelos relógios de ponto._

##### O caminho do projeto é "C:\AutoPonto"

![Image](https://github.com/user-attachments/assets/a3fac709-39a9-4856-b4a7-1f6057db0af0)

## ESTRUTURA DA PASTA RAÍZ (_C:\AutoPonto_)
![Image](https://github.com/user-attachments/assets/e8371d10-f817-465a-b327-16a1805d47d5)

### __ESTRUTURA DA PASTA bat:__ 
![Image](https://github.com/user-attachments/assets/2567d2af-ec79-4d85-9a8a-feb9ecabc421)

Esta pasta guarda os arquivos ".bat" e ".vbs" que são executados pelo agendador de tarefas. Os arquivos ".bat" executam os arquivos python que têm como função abrir o navegador simulado e baixar o AFD do relógio que estiver instanciado. Já os arquivos ".vbs" servem basicamente para executar os arquivos ".bat" sem mostrar as janelas pretas do terminal de comandos.

Veja o exemplo de um arquivo ".bat" e um ".vbs" (respectivamente) dentro da pasta "bat":
![Image](https://github.com/user-attachments/assets/a848c17d-17b0-418e-9c7b-8435e7d77f39)
![Image](https://github.com/user-attachments/assets/c0d8faed-d399-457e-88a1-482b2a943d53)

Dentro da pasta "bat", temos a pasta "mov". Os arquivos dentro desta pasta são executador pelo agendador logo após o fim do download de todos os AFD. Eles servem para mover os AFD da pasta "C:\Users\integracao\Downloads\" para o endereço em servidor "\\192.168.1.254\ponto\AFD\".

Veja o exemplo de um arquivo ".bat" e um ".vbs" (respectivamente) mas afora dentro dentro da pasta "mov":

![Image](https://github.com/user-attachments/assets/811f6a68-1508-437a-bd17-3700ec965b81)

![Image](https://github.com/user-attachments/assets/00348f6d-602f-4a43-9248-c0096c8d8bd9)


### __ESTRUTURA DA PASTA schedules:__ 
![Image](https://github.com/user-attachments/assets/2be80a3c-f3ca-40c7-9db2-63ab2b795c69)

Pasta que guarda os XML usados pelo agendador, não se faz necessário o entendimento destes arquivos, pois o próprio agendador do windows os gera, é so criá-los exporta-los pelo agendador de tarefas.

### __ESTRUTURA DA PASTA src:__ 
![Image](https://github.com/user-attachments/assets/ed6042ce-b239-4ba9-942a-c9e6fe5d18a3)

Pasta com os arquivos python, eles levam os scripts que fazem todo o processo de abertura do navegador simulado (em modo headless, ou seja, sem que o usuário veja a interface gráfica), login no Control_ID e download do AFD.

##### Veja a seguir uma parte da estrutura de um destes scripts.
![Image](https://github.com/user-attachments/assets/8d053351-aca3-404b-bc5c-3f6afd340c73)
Este é o cabeçalho, com as importações das bibliotecas necessárias. Como você pode ver, há no cabeçalho de cada arquivo, o ip do relógio de ponto que será alvo do script.

![Image](https://github.com/user-attachments/assets/2308da2c-93a5-4975-af7a-1b9f80bf66ff)
Acima você vê parâmetros necessários para o funcionamento do script; mas quero ressaltar o trecho abaixo, que pode ser confuso à primeira vista:

![Image](https://github.com/user-attachments/assets/ac2a2229-2c87-4d11-9ee1-f5aad1d59a72)
A variável "service" recebe o caminho exato do chromedriver, que simula o navegador headless. Sem este driver, não há possíbilidade de funcionar.

As variáveis "lgn" e "cidfrtlz" recebem a senha e o usuário usados para download do AFD; no entanto, como são dados sansíveis, estão criptografados. Como este é um documento público, para mais explicações sobre esta pequena criptografia, entre em contato comigo. Não é nada complexo, mas deixar senhas e usuários expostos em códigos fonte não seria uma boa opção.

### _LOGS E ERROS_:

![Image](https://github.com/user-attachments/assets/2069a580-f766-438f-845f-9302979c202a)

Um log é grado para cada relógio cada vez que o script for rodado, seja manualmente ou pelo agendador de tarefas.

## ESTRUTURA DO PROJETO NO AGENDADOR DE TAREFAS:
### _CAMINHO:_
![Image](https://github.com/user-attachments/assets/e78fb305-6367-4ae9-abc2-f83a7d59a701)

### _CONFIGURAÇÕES PADRÃO DOS AGENDAMENTOS "Mov":_

![Image](https://github.com/user-attachments/assets/e262b46a-46a8-4f03-b28b-27e27be514be)

![Image](https://github.com/user-attachments/assets/b73b89e2-01b7-4fd4-aa75-b308b1d22210)

![Image](https://github.com/user-attachments/assets/ede0aecb-ba2a-4c9f-bff4-df168d724b7b)

![Image](https://github.com/user-attachments/assets/d478fb57-2188-471c-b46e-deb466c7f4ec)

![Image](https://github.com/user-attachments/assets/115797c2-f993-4ff8-88a1-97cc3d4d3da9)

![Image](https://github.com/user-attachments/assets/4a5ec84f-2ed5-45c5-ab35-f3754849c758)

### _CONFIGURAÇÕES PADRÃO DOS AGENDAMENTOS "Schedule":_
![Image](https://github.com/user-attachments/assets/60bc12c7-ff39-460f-9cbb-3f4c0f11f4c0)

![Image](https://github.com/user-attachments/assets/e2115fa9-471b-4b30-a823-a84c823368b3)

![Image](https://github.com/user-attachments/assets/1155cfbb-876d-4852-8947-a275c4422559)

![Image](https://github.com/user-attachments/assets/38bc7038-db0b-42ed-a39d-9574fd045f03)

![Image](https://github.com/user-attachments/assets/9f0d2cc8-b07f-46da-9b72-95de60c72b7a)

![Image](https://github.com/user-attachments/assets/599b6ac7-81cf-402c-91fe-6d48aa78312b)

### Se tudo estiver feito corretamente, ao final do dia, devem haver 6 arquivos AFD com horários proximos um do outro, no caminho "\\192.168.1,254\ponto\AFD", como na imagem abaixo:

![Image](https://github.com/user-attachments/assets/a5aa1a1c-050e-4f50-b3ef-4ab4f9cc40e7)

Este projeto não entrou em vigor porque necessita de ajustes que só são previsíveis se o desenvolvimento caminhar lado a lado com o ambiente de destino, que, neste caso, era a rotina de ponto do protheus.

![Image](https://github.com/user-attachments/assets/d4f8df59-f0ae-4b0e-82dc-33812a76861f)
![Image](https://github.com/user-attachments/assets/a3fac709-39a9-4856-b4a7-1f6057db0af0)
