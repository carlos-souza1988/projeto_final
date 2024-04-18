Projeto Final do Grupo 2

🚀 Começando

Estas instruções permitirão que você obtenha uma cópia do projeto em operação em sua máquina local para fins de desenvolvimento e teste.

Consulte Implantação para saber como implantar o projeto.

📋 Pré-requisitos
Programas neceessários:

Visual Studio Code
Python 3

🔧 Instalação
Necessário instalar as seguintes bibliotecas:

pandas
numpy
sqlite3
plyer
requests
tqdm Para instalar as bibliotecas, fazemos da seguinte forma: Exemplo: pip install pandas

⚙️ Executando os testes
Explicar como executar os testes automatizados para este sistema.

🔩 Analise os testes de ponta a ponta Explique que eles verificam esses testes e porquê.

Dar exemplos ⌨️ E testes de estilo de acordo Explique que eles verificam esses testes e porquê.

Dar exemplos

def alerta(nivel, base, etapa, erro=""):
    """
    Alerta de falha de carregamento de base de dados.

    Args:
        nivel (int): Nível de alerta (1, 2 ou 3).
        base (str): Nome da base de dados.
        etapa (str): Etapa do carregamento.
        erro (str, optional): Mensagem de erro (padrão: ""). 

    Returns:
        None
    """
    now = str(datetime.now())

    msg = f"Falha no carregamento da base {base} na etapa {etapa}.\n{now}\n{erro}"

    if nivel == 1:
        title = 'ATENÇÃO: Alerta Baixo'
    elif nivel == 2:
        title = 'ATENÇÃO: Alerta Médio'
    elif nivel == 3:
        title = 'ATENÇÃO: Alerta Alto'
    else:
        print("Nível", nivel, "não disponível!")

    notification.notify(
        title=title,
        message=msg,
        app_name='alerta',
        timeout=10
    )

Este código define uma função chamada alerta que emite notificações de alerta em caso de falhas no carregamento de bases de dados. Aqui estão as principais informações sobre a função:

Parâmetros:
* nivel: Nível de alerta (1, 2 ou 3).
* base: Nome da base de dados.
* etapa: Etapa do carregamento.
* erro (opcional): Mensagem de erro (padrão: “”).

Retorno:
* A função não retorna nenhum valor explicitamente (retorna None).

Funcionamento:
* A função obtém a data e hora atual.
* Constrói uma mensagem de alerta com informações sobre a base de dados, etapa e erro (se houver).
* Determina o título da notificação com base no nível de alerta.
* Emite uma notificação usando a biblioteca notification com o título, mensagem e um tempo limite de 10 segundos.

Lembre-se de adaptar o código conforme necessário para o seu contexto específico. Certifique-se de importar a biblioteca datetime e configurar a biblioteca de notificações corretamente para o seu ambiente.

📦 Implantação
Adicione notas adicionais sobre como implantar isso em um sistema ativo

🛠️ Construído com
https://code.visualstudio.com/ -> Visual Studio Code
https://www.python.org/downloads/ -> Python 3
https://pokeapi.co/ -> Api Pokemon

📌 Versão
Nós usamos o arquivo requirements.txt do repositório para controle de versão.

✒️ Autores
Bruno Lapolli
Carlos Eduardo Munhoz
Carlos Henrique de Souza
Italo Nhã

🎁 Expressões de gratidão
O projeto foi um grande desafio para toda nossa equipe, lidar com tratamentos e análise de dados é algo muito interessante e desafiador. Buscamos extrair da melhor forma e prática os dados da nossa api.
=======
# 📋 Pré-requisitos
Programas neceessários:
 - Visual Studio Code
 - Python 3

# 🔧 Instalação
 Necessário instalar as seguintes bibliotecas:
 - pandas
 - numpy
 - sqlite3
 - plyer
 - requests
 - tqdm
Para instalar as bibliotecas, fazemos da seguinte forma:
Exemplo: pip install pandas

# ⚙️ Executando os testes
Explicar como executar os testes automatizados para este sistema.

🔩 Analise os testes de ponta a ponta
Explique que eles verificam esses testes e porquê.

Dar exemplos
⌨️ E testes de estilo de acordo
Explique que eles verificam esses testes e porquê.

Dar exemplos

# 📦 Implantação
Adicione notas adicionais sobre como implantar isso em um sistema ativo

# 🛠️ Construído com
https://code.visualstudio.com/     -> Visual Studio Code                                      
https://www.python.org/downloads/  -> Python 3                                               
https://pokeapi.co/                -> Api Pokemon

# 📌 Versão
Nós usamos o arquivo requirements.txt do repositório para controle de versão.

# ✒️ Autores
 - Bruno Lapolli
 - Carlos Eduardo Munhoz
 - Carlos Henrique de Souza
 - Italo Nhã

# 🎁 Expressões de gratidão
O projeto foi um grande desafio para toda nossa equipe, lidar com tratamentos e análise de dados é algo muito interessante e desafiador. Buscamos extrair da melhor forma e prática os dados da nossa api.
