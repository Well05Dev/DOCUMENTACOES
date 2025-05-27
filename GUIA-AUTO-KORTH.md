# AUTOMATIZADOR KORTH
### _Um guia de acesso ao projeto em funcionamento da automação do KORTH._

![Image](https://github.com/user-attachments/assets/d4f8df59-f0ae-4b0e-82dc-33812a76861f)
![Image](https://github.com/user-attachments/assets/d57c0f0d-5e98-4d2b-966f-bb96024ec959)

## ESTRUTURA DA PASTA (_C:\korth-automatizador_)
   ![Image](https://github.com/user-attachments/assets/6f7570fd-db90-4719-992f-3bdd18f2246f)

### __pycache:__ 
Pasta gerada automaticamente pelo uso das bibliotecas.

### __img:__ 
Pasta com as referências de botões a serem clicados.

### __schedules:__ 
Pasta com os arquivos XML de referência para o agendador de tarefas nativo do windows

### __attmonitor.py:__ 
Script destinado a reiniciar o monitor de tanques após a sincronização automatica, visando evitar bugs visuais.

### __closeapp.py:__
Micro biblioteca usando subprocess para encerrar os aplicativos neste projeto quando necessário. 

### __popup.py:__
Funções que serão usadas para apresentar popups notificando a futura atualização automática. Não é fundamental para o funcionamento do código, mas é uma forma de evitar que haja interferência de algum possível usuário no processo.

### __restartmonitor.bat:__
Arquivo bat que será alvo do agendador de tarefas quando estiver no horário da execução.

### __screenreader.py:__
Biblioteca feita por mim, que trabalha toda a lógica de visão computacional para sincronizar o KORTH. utiliza as bibliotecas "pyautogui" e "time", que são __FUNDAMENTAIS__ para o funcionamento da automação.

![Image](https://github.com/user-attachments/assets/c49f21c3-8855-4b72-8551-de7d964fc9a2)

Este parâmetro está setado para falso. Com ele setado para verdadeiro, se o cursor do mouse se aproximar das bordas em meio a execução, o processo será abortado. O arquivo está comentado com explicações e instruções.

##### __A função "CheckIfExists"__ 
que faz a busca da imagem referenciada na tela. Ela recebe dois parâmetros: src_img" e "confidence_img". 

![Image](https://github.com/user-attachments/assets/ef7901ae-db44-44de-b820-f7a55b3e8d61)

"src_img" recebe como parâmetro o caminho da imagem. "confidence_img" recebe como parâmetro o nível de fidelidade buscado entre a imagem a ser buscada e a imagem na tela. Este segundo parâmetro leva como mínimo 0 e como máximo 1, mas não é booleano. De acordo com meus testes, o nível de fidelidade ideal para este projeto é 0.9.

##### __A função "Click"__ 
também faz a busca da imagem referenciada na tela, mas a diferença dela, é que ao invés de apenas buscar e retornar se a imagem existe ou não, ela verifica se existe e clica (se existir), e, por último, retorna o corpo do email em string com os status da execução da função. Ela também recebe dois parâmetros: src_img" e "confidence_img". 

![Image](https://github.com/user-attachments/assets/bdbe5149-1b04-4111-a4f2-d53884f925f9)

##### __A função "DoubleClick"__ 
O nome é auto-explicativo. Tem o mesmo intuito da função anterior, mas ao invés de um click, ela dá dois.

![Image](https://github.com/user-attachments/assets/aa05e1ca-3dbc-49fe-aebf-6daac97e6c9b)

### __sendemail.py:__

##### __Micro biblioteca para envio de email.__

![Image](https://github.com/user-attachments/assets/c39d8bfe-5854-4a5b-80c0-b738b57fa333)

também montada por mim para receber o corpo montado do email e fazer o envio com o status da execução, horários, datas e um print da tela para certificar a sincronização.

### __sync.bat:__

##### __Arquivo .bat.__
Será o alvo do agendador de tarefas, tendo como objetivo executar o arquivo "sync1.py"
![Image](https://github.com/user-attachments/assets/009fc363-80da-472f-ba65-f30fa1c38c5d)

### __sync1.py:__

##### __Arquivo main, que amarra todos os outros componentes.__
![Image](https://github.com/user-attachments/assets/509ec0e6-fd1e-4e26-a5fb-c06e649659da)

Não há necessidade de explicá-lo; seu funcionamento é simples, busca as funções das bibliotecas criadas por mim, e das outras listadas no cabeçalho do documento.

# REFERENTE AO AGENDADOR DE TAREFAS:
![Image](https://github.com/user-attachments/assets/f25c5989-5853-418f-be40-1ad7bfd89b8b)

### AGENDAMENTO "REINICIAR MONITOR":
![Image](https://github.com/user-attachments/assets/cc92f3cb-d428-4c89-816b-cb197a0db561)

##### SUAS CONFIGURAÇÕES:

![Image](https://github.com/user-attachments/assets/96c6790a-eafa-4699-a968-047a28e9a238)

![Image](https://github.com/user-attachments/assets/10347c81-30d7-40b9-b227-6788af69adc5)

![Image](https://github.com/user-attachments/assets/f84bd27c-acf6-4015-8642-b12c9cce476f)

![Image](https://github.com/user-attachments/assets/cedb397f-0c35-4966-b0ee-dd10ce1cf873)

![Image](https://github.com/user-attachments/assets/b63d546c-f5db-4b2a-916f-e5a77f40278f)

### AGENDAMENTO "SINCRONIZAR KORTH":
![Image](https://github.com/user-attachments/assets/64544020-1c5d-46af-92a8-0039b36ee06f)

##### SUAS CONFIGURAÇÕES:

![Image](https://github.com/user-attachments/assets/203e7bc8-4182-4cb9-a200-6f42b679576c)

![Image](https://github.com/user-attachments/assets/6d4ef2a5-bcb4-4d92-b3d2-bcac7c902537)

![Image](https://github.com/user-attachments/assets/7cd2e691-076b-48d5-9d6f-18e75186c661)

![Image](https://github.com/user-attachments/assets/ff99be20-5e01-48ab-ad28-887f71f3849a)

![Image](https://github.com/user-attachments/assets/57cf30b2-b115-4320-a8a6-8b1a3fe5fdfd)



### __ATENÇÃO!__ 
### Para o funcionamento deste automatizador, é imprescindível que haja um monitor conectado ao servidor que rodará o script. Este monitor serve unicamente para retornar imagem, mas é simplesmente fundamental.
#### Além disso, precisa estar com algum usuário logado no windows. (neste caso, "Integracoes unilink")

![Image](https://github.com/user-attachments/assets/d4f8df59-f0ae-4b0e-82dc-33812a76861f)
![Image](https://github.com/user-attachments/assets/d57c0f0d-5e98-4d2b-966f-bb96024ec959)
