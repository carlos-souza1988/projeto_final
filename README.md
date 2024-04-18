# Projeto Final do Grupo 2

## 🚀 Começando
Estas instruções permitirão que você obtenha uma cópia do projeto em operação em sua máquina local para fins de desenvolvimento e teste.

Consulte Implantação para saber como implantar o projeto.

## 📋 Pré-requisitos
Programas neceessários:

* Visual Studio Code
* Python 3

## 🔧 Instalação
Necessário instalar as seguintes bibliotecas:

* pandas
* numpy
* sqlite3
* plyer
* requests
* tqdm 
Para instalar as bibliotecas, fazemos da seguinte forma: Exemplo: pip install pandas

## ⚙️ Executando os testes

## Alerta
Este código define uma função chamada alerta que serve para emitir notificações de alerta em caso de falhas no carregamento de bases de dados. Explicando os principais pontos:

1. **Função `alerta(nivel, base, etapa, erro)`**:
    - Esta função é responsável por enviar alertas em caso de falha no carregamento de uma base de dados.
    - Aqui estão os passos que ela realiza:
        - Obtém a data e hora atual.
        - Monta uma mensagem de alerta que inclui o nome da base de dados, a etapa do processo e, opcionalmente, uma descrição do erro.
        - Com base no nível de alerta fornecido (1, 2 ou 3), define um título apropriado.
        - Utiliza uma biblioteca chamada `notification` para exibir o alerta na tela do usuário.
        - O alerta permanece visível por 10 segundos.

    Em resumo, essa função é usada para notificar os usuários sobre problemas relacionados ao carregamento de dados. Ela é útil para monitorar processos e garantir que os administradores sejam informados quando algo não está funcionando corretamente.

## Conexão com as as APIs e Carregamento para as Stages

1. **Função `get_json_api(url)`**:
    - Esta função é usada para fazer uma solicitação HTTP GET a uma URL específica.
    - Aqui estão os passos que ela executa:
        - Faz uma requisição GET à URL fornecida.
        - Verifica se o código de status da resposta é 200 (o que significa que a solicitação foi bem-sucedida).
        - Se for 200, converte os dados da resposta em um objeto JSON e o retorna.
        - Caso contrário, lança uma exceção com informações sobre o erro ocorrido.

    Em resumo, essa função é útil para obter dados em formato JSON de uma API ou serviço da web. Ela é usada quando precisamos buscar informações específicas de uma URL.

2. **Função `get_base_pokemons_url()`**:
    - Esta função é usada para obter informações sobre URLs relacionados aos pokémons.
    - Aqui estão os passos que ela executa:
        - Começa com uma URL inicial: <span style="color: #007acc; font-weight: bold;">"https://pokeapi.co/api/v2/pokemon"</span>.
        - Cria um <span style="color: #007acc; font-weight: bold;">DataFrame vazio</span> chamado <span style="color: #007acc; font-weight: bold;">`df_pokemons_full`</span>.
        - Enquanto houver uma próxima URL (ou seja, mais páginas de dados), faz o seguinte:
            - Faz uma solicitação HTTP GET à URL atual.
            - Converte os dados da resposta em um objeto JSON.
            - Cria um <span style="color: #007acc; font-weight: bold;">DataFrame</span> chamado <span style="color: #007acc; font-weight: bold;">`df_pokemons`</span> com os resultados.
            - Adiciona os dados do <span style="color: #007acc; font-weight: bold;">`df_pokemons`</span> ao <span style="color: #007acc; font-weight: bold;">`df_pokemons_full`</span>.
            - Obtém a próxima URL da resposta JSON para continuar buscando mais dados.
        - Finalmente, retorna o <span style="color: #007acc; font-weight: bold;">`df_pokemons_full`</span> completo com todas as informações dos URLs dos pokémons.

    Em resumo, essa função é usada para coletar informações sobre os pokémons a partir de uma API, organizando os dados em um formato tabular para análise posterior.

3. **Função `get_base_habilidades_url()`**:
    - Esta função é usada para obter informações sobre URLs relacionados às habilidades dos pokémons.
    - Aqui estão os passos que ela executa:
        - Começa com uma URL inicial: <span style="color: #007acc; font-weight: bold;">"https://pokeapi.co/api/v2/ability"</span>.
        - Cria um <span style="color: #007acc; font-weight: bold;">DataFrame vazio</span> chamado <span style="color: #007acc; font-weight: bold;">`df_habilidades_full`</span>.
        - Enquanto houver uma próxima URL (ou seja, mais páginas de dados), faz o seguinte:
            - Faz uma solicitação HTTP GET à URL atual.
            - Converte os dados da resposta em um objeto JSON.
            - Cria um <span style="color: #007acc; font-weight: bold;">DataFrame</span> chamado <span style="color: #007acc; font-weight: bold;">`df_habilidade`</span> com os resultados.
            - Adiciona os dados do <span style="color: #007acc; font-weight: bold;">`df_habilidade`</span> ao <span style="color: #007acc; font-weight: bold;">`df_habilidades_full`</span>.
            - Obtém a próxima URL da resposta JSON para continuar buscando mais dados.
        - Finalmente, retorna o <span style="color: #007acc; font-weight: bold;">`df_habilidades_full`</span> completo com todas as informações dos URLs das habilidades.

4. **Função `get_base_especies_url()`**:
    - Esta função é usada para obter informações sobre URLs relacionados às espécies de pokémons.
    - Ela segue uma lógica semelhante à função anterior, mas busca dados específicos relacionados às espécies.
    - Retorna um <span style="color: #007acc; font-weight: bold;">DataFrame</span> chamado <span style="color: #007acc; font-weight: bold;">`df_especie_full`</span> com todas as informações dos URLs das espécies.

    Em resumo, essas funções são usadas para coletar informações importantes sobre habilidades e espécies de pokémons a partir de uma API, organizando os dados em um formato tabular para análise posterior.

5. **Função `get_base_pokemons()`**:
    - Esta função é usada para obter informações detalhadas sobre os pokémons.
    - Aqui estão os passos que ela executa:
        - Carrega os dados da tabela chamada <span style="color: #007acc; font-weight: bold;">"pokemons_url"</span>.
        - Cria um <span style="color: #007acc; font-weight: bold;">DataFrame vazio</span> chamado <span style="color: #007acc; font-weight: bold;">`df_pokemons_full`</span>.
        - Para cada URL de pokémon na tabela:
            - Faz uma solicitação HTTP GET à URL.
            - Converte os dados da resposta em um objeto JSON.
            - Extrai informações como ID, nome, habilidades, altura, peso e experiência base.
            - Cria uma <span style="color: #007acc; font-weight: bold;">Série</span> chamada <span style="color: #007acc; font-weight: bold;">`sr_pokemon`</span> com essas informações.
            - Adiciona os dados do <span style="color: #007acc; font-weight: bold;">`sr_pokemon`</span> ao <span style="color: #007acc; font-weight: bold;">`df_pokemons_full`</span>.
        - Finalmente, retorna o <span style="color: #007acc; font-weight: bold;">`df_pokemons_full`</span> completo com todas as informações dos pokémons.

    Em resumo, essa função é usada para coletar e organizar dados sobre os pokémons, incluindo detalhes como habilidades, altura e peso.

6. **Função `get_base_habilidades()`**:
    - Essa função é usada para obter informações detalhadas sobre as habilidades dos pokémons.
    - Aqui estão os passos que ela executa:
        - Carrega os dados da tabela chamada **"habilidades_url"**.
        - Cria um **DataFrame vazio** chamado **`df_habilidades_full`**.
        - Para cada URL de habilidade na tabela:
            - Faz uma solicitação HTTP GET à URL.
            - Converte os dados da resposta em um objeto JSON.
            - Extrai informações como ID, nome, geração, se é uma série principal e o efeito da habilidade.
            - Cria uma **Série** chamada **`sr_habilidade`** com essas informações.
            - Adiciona os dados da **`sr_habilidade`** ao **`df_habilidades_full`**.
        - Finalmente, retorna o **`df_habilidades_full`** completo com todas as informações das habilidades.

7. **Função `get_base_especies()`**:
    - Essa função é usada para obter informações sobre as espécies de pokémons.
    - Ela segue uma lógica semelhante à função anterior, mas busca dados específicos relacionados às espécies.
    - Retorna um **DataFrame** chamado **`df_especie_full`** com todas as informações das espécies.

Em resumo, essas funções são usadas para coletar e organizar dados importantes sobre habilidades e espécies de pokémons.

## Banco de Dados
Este código é escrito em Python e lida com banco de dados SQLite. Explicando as partes:

1. **Função `tabelas_bd()`**:
    - Esta função se conecta ao banco de dados chamado `'pokemon.db'`.
    - Em seguida, executa uma consulta SQL que retorna os nomes das tabelas presentes no esquema do banco de dados.
    - Os nomes das tabelas são armazenados em um <span style="color: #007acc; font-weight: bold;">DataFrame</span> (uma estrutura de dados tabular) chamado <span style="color: #007acc; font-weight: bold;">`schema`</span>.
    - Por fim, a conexão com o banco de dados é fechada e o <span style="color: #007acc; font-weight: bold;">`schema`</span> é retornado.

2. **Função `salva_bd(df, nome_tabela)`**:
    - Recebe dois argumentos: um <span style="color: #007acc; font-weight: bold;">DataFrame</span> chamado <span style="color: #007acc; font-weight: bold;">`df`</span> e o nome de uma tabela chamada <span style="color: #007acc; font-weight: bold;">`nome_tabela`</span>.
    - Conecta-se ao banco de dados <span style="color: #007acc; font-weight: bold;">'pokemon.db'</span>.
    - Escreve o conteúdo do <span style="color: #007acc; font-weight: bold;">`df`</span> na tabela especificada (<span style="color: #007acc; font-weight: bold;">`nome_tabela`</span>).
    - Se a tabela já existir, ela é substituída (<span style="color: #007acc; font-weight: bold;">`if_exists='replace'`</span>).
    - A conexão com o banco de dados é fechada e a função retorna <span style="color: #007acc; font-weight: bold;">`True`</span>.

3. **Função `carrega_bd(nome_tabela)`**:
    - Recebe o nome de uma tabela chamada <span style="color: #007acc; font-weight: bold;">`nome_tabela`</span>.
    - Conecta-se ao banco de dados <span style="color: #007acc; font-weight: bold;">'pokemon.db'</span>.
    - Executa uma consulta SQL que seleciona todos os registros da tabela especificada.
    - Os resultados da consulta são convertidos em um <span style="color: #007acc; font-weight: bold;">DataFrame</span> chamado <span style="color: #007acc; font-weight: bold;">`df`</span>.
    - A conexão com o banco de dados é fechada e o <span style="color: #007acc; font-weight: bold;">`df`</span> é retornado.

Em resumo, essas funções permitem interagir com um banco de dados SQLite, consultando informações sobre tabelas, salvando dados em tabelas e carregando dados de tabelas em DataFrames. É uma maneira de manipular dados de forma organizada e eficiente.


## Extração

1. **Função `etapa_extracao()`**:
    - Esta função é responsável por realizar a extração de dados de diferentes bases.
    - Aqui estão os passos que ela executa:
        - **Base `pokemons_url`**:
            - Obtém informações sobre os URLs relacionados aos pokémons.
            - Se ocorrer algum erro, um alerta de nível alto é acionado.
        - **Base `habilidades_url`**:
            - Obtém informações sobre os URLs relacionados às habilidades dos pokémons.
            - Se ocorrer algum erro, um alerta de nível alto é acionado.
        - **Base `especie_url`**:
            - Obtém informações sobre os URLs relacionados às espécies de pokémons.
            - Se ocorrer algum erro, um alerta de nível alto é acionado.
        - **Base `pokemons`**:
            - Obtém dados completos sobre os pokémons.
            - Se ocorrer algum erro, um alerta de nível alto é acionado.
        - **Base `habilidades`**:
            - Obtém dados completos sobre as habilidades dos pokémons.
            - Se ocorrer algum erro, um alerta de nível alto é acionado.
        - **Base `especieses`**:
            - Obtém dados completos sobre as especies dos pokémons.
            - Se ocorrer algum erro, um alerta de nível alto é acionado.

    Em resumo, essa função é usada para extrair dados importantes relacionados aos pokémons e suas habilidades, garantindo que qualquer problema seja notificado aos administradores. 😊

## Transformação e Carga

1. **Função `tranformacao_pokemon()`**:
    - Esta função é responsável por transformar os dados relacionados aos pokémons.
    - Aqui estão os passos que ela executa:
        - Carrega os dados da tabela chamada **"stage_pokemons"**.
        - Preenche quaisquer valores ausentes na tabela de pokémons com zero na coluna **"base_experience"**.
        - Converte os tipos de dados das colunas para os seguintes formatos:
            - **pokemon_id**: inteiro
            - **name**: string (texto)
            - **height**: inteiro
            - **weight**: inteiro
            - **base_experience**: número decimal (ponto flutuante)
        - Seleciona apenas as colunas relevantes: **pokemon_id**, **name**, **height**, **weight** e **base_experience**.
        - Salva a tabela tratada de pokémons.
        - Se ocorrer algum erro durante esse processo, um alerta de nível médio é acionado.

    Em resumo, essa função é usada para limpar e preparar os dados dos pokémons, garantindo que estejam no formato correto para análise posterior.

2. **Função `tranformacao_habilidades()`**:
    - Esta função é responsável por transformar os dados relacionados às habilidades dos pokémons.
    - Aqui estão os passos que ela executa:
        - Carrega os dados da tabela chamada **"stage_habilidades"**.
        - Renomeia as colunas para torná-las mais descritivas: **"name"** é renomeada para **"ability_name"** e **"effect"** é renomeada para **"ability_effect"**.
        - Seleciona apenas as colunas relevantes: **habilidade_id**, **ability_name** e **ability_effect**.
        - Converte os tipos de dados das colunas para os seguintes formatos:
            - **habilidade_id**: inteiro
            - **ability_name**: texto (string)
            - **ability_effect**: texto (string)
        - Salva a tabela tratada de habilidades.
        - Se ocorrer algum erro durante esse processo, um alerta de nível médio é acionado.

    Em resumo, essa função é usada para limpar e preparar os dados das habilidades dos pokémons, garantindo que estejam no formato correto para análise posterior.

3. **Função `tranformacao_pokemons_habilidades()`**:
    - Essa função é responsável por transformar os dados relacionados às habilidades dos pokémons.
    - Aqui estão os passos que ela executa:
        - Carrega os dados da tabela chamada **"stage_pokemons"**.
        - Abre as linhas por habilidade, ou seja, cria uma nova linha para cada habilidade de um pokémon.
        - Busca o ID das habilidades a partir das URLs das habilidades.
        - Remove linhas vazias (caso existam).
        - Remove linhas duplicadas.
        - Converte os tipos de dados das colunas para os seguintes formatos:
            - **pokemon_id**: inteiro
            - **habilidade_id**: inteiro
        - Salva a tabela tratada de pokémons e habilidades.
        - Se ocorrer algum erro durante esse processo, um alerta de nível médio é acionado.

    Em resumo, essa função organiza os dados das habilidades dos pokémons, garantindo que estejam no formato correto para análise posterior.

4. **Função `tranformacao_especies()`**:
    - Essa função é responsável por transformar os dados relacionados às espécies de pokémons.
    - Aqui estão os passos que ela executa:
        - Carrega os dados da tabela chamada **"stage_especies"**.
        - Seleciona apenas as colunas relevantes: **especie_id**, **name**, **color** e **growth_rate**.
        - Remove linhas vazias (caso existam).
        - Converte os tipos de dados das colunas para os seguintes formatos:
            - **especie_id**: inteiro
            - **name**: texto (string)
            - **color**: texto (string)
            - **growth_rate**: texto (string)
        - Salva a tabela tratada de espécies.
        - Se ocorrer algum erro durante esse processo, um alerta de nível médio é acionado.

    Em resumo, essa função organiza os dados das espécies de pokémons, garantindo que estejam no formato correto para análise posterior.

5. **Função `tranformacao_pokemons_especies()`**:
    - Essa função é responsável por transformar os dados relacionados às espécies de pokémons.
    - Aqui estão os passos que ela executa:
        - Carrega os dados da tabela chamada **"stage_pokemons"**.
        - Busca o ID das espécies a partir das URLs das espécies.
        - Remove linhas vazias (caso existam).
        - Remove linhas duplicadas.
        - Converte os tipos de dados das colunas para os seguintes formatos:
            - **pokemon_id**: inteiro
            - **especie_id**: inteiro
        - Salva a tabela tratada de pokémons e espécies.
        - Se ocorrer algum erro durante esse processo, um alerta de nível médio é acionado.

Em resumo, essa função organiza os dados das espécies de pokémons, garantindo que estejam no formato correto para análise posterior.

## 📦 Implantação
Objetivo do projeto foi extrair as informações e buscar a base de pokemons da api, com suas habilidades e suas bases especiais.
## 🛠️ Construído com
* https://code.visualstudio.com/ -> Visual Studio Code
* https://www.python.org/downloads/ -> Python 3
* https://pokeapi.co/ -> Api Pokemon

## 📌 Versão
Nós usamos o arquivo requirements.txt do repositório para controle de versão.

## ✒️ Autores
* Bruno Lapolli
* Carlos Eduardo Munhoz
* Carlos Henrique de Souza
* Italo Nhã

## 🎁 Expressões de gratidão
O projeto foi um grande desafio para toda nossa equipe, lidar com tratamentos e análise de dados é algo muito interessante e desafiador. Buscamos extrair da melhor forma e prática os dados da nossa api.
