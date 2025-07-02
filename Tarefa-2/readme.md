# 🍁 I2A2-ai 🍁
#Grupo CONNOR  
[Jeferson Nunes](https://www.linkedin.com/in/nunesjeferson/) | Mardem Guilherme | Fábio Oliveira | Carlos Baldisserra

# 🔍 [AgenteFiscal Chat](https://johnconnor.app.n8n.cloud/webhook/b46b73d7-b028-4f31-83de-ff97d29fdbe8/chat)

## Objetivo da atividade  
A atividade tem por objetivo criar um ou mais agentes que tornem possível a um usuário realizar perguntas sobre os arquivos CSV disponibilizados.  
Por exemplo: Qual é o fornecedor que teve maior montante recebido? Qual item teve maior volume entregue (em quantidade)? E assim por diante.  

## Recusos
Foi disponibilizado um arquivo chamado [202401_NFs.zip](https://drive.google.com/drive/folders/1EYgJrhf3BKHypPQLT5xwTHhsHa2BYMFt), o qual pode ser baixado por aqui ou através do link constante na página de arquivos do site do curso.  

Neste arquivo você encontrará:

202401_NFs_Cabecalho.csv – O cabeçalho de 100 notas fiscais selecionadas aleatoriamente do arquivo de notas fiscais do mês de janeiro/2024, disponibilizado pelo Tribunal de Contas da União e,

202401_NFs_Itens.csv – Os itens correspondentes das 100 notas fiscais selecionadas.

Ambos os arquivos estão em formato csv. Os campos estão separados por vírgulas e o separador de casas decimas dos valores numéricos é ponto. As datas estão no formato AAAA-MM-DD HH:MN:SS, onde AAAA é o ano com 4 algarismos, MM é o mês com 2 algarismos, DD é o dia com dois algarismos, HH é a hora com 2 algarismos, MN são os minutos com 2 algarismos e SS são os segundos com 2 algarismos.

## O que deve ser feito:

A solução entregue deverá ter uma interface onde o usuário irá informar sua pergunta e o agente irá gerar a resposta desejada.  
Para tanto, o agente deverá descompactar os arquivos, selecionar o arquivo desejado, carregar os dados e fazer as queries e gerar a resposta para o usuário.  
Para construir seus agentes, vocês podem optar por escrever programas em Python ou utilizar ferramentas NoCode/LowCode.  
Sugerimos os seguintes frameworks/ferramentas:  
·  https://autogenhub.github.io/autogen/  
·  https://ai.pydantic.dev/  
·  https://www.langchain.com/  
·  https://www.llamaindex.ai/  
·  https://www.crewai.com/  
·  https://n8n.io/  📌  
·  https://www.langflow.org/

# 💻 Entrega
Ao final de suas atividades, vocês devem gerar um relatório descrevendo:

## 1.     A framework escolhida
Escolhemos o [n8n](https://n8n.io/), o motvo foi por se tratar de uma ferramenta lowcode/nocode. Apesar de termos um integrande com certa experiência em dados, não temos nenhum programador no grupo.

## 2.     Como a solução foi estruturada
![image](https://github.com/user-attachments/assets/d6c98d71-784b-4e1c-9a80-a7ee4db25f25)
Seguimos o passo-a-passo exigido para a entrega:  
descompactar os arquivos → selecionar o arquivo desejado → carregar os dados → fazer as queries → gerar a resposta para o usuário

## 3.     Pelo menos 4 perguntas com as respectivas respostas.

### 1 - Qual o valor total das notas?
    
Entendi que você quer saber o valor total de todas as notas fiscais.

Resultados: O valor total de todas as notas fiscais é de R$ 3.371.754,84.

Explicação: Para chegar a este resultado, somei a coluna "VALOR NOTA FISCAL" da tabela ai_table_cabecalho.


### 2 - Qual nota de maior valor total?

Entendi que você deseja saber qual é a nota fiscal de maior valor total.

Resultados: A nota fiscal de maior valor é a de número 135717, com um valor total de R$ 1.292.418,75.

Explicação: Para chegar a este resultado, selecionei o número da nota fiscal e o valor da nota fiscal da tabela ai_table_cabecalho e ordenei os resultados pelo valor da nota fiscal em ordem decrescente, pegando o primeiro resultado.


### 3 - Qual empresa mais emitiu notas?

Entendi que você quer saber qual empresa emitiu o maior número de notas fiscais.

Resultados: A empresa que mais emitiu notas fiscais foi "EMPRES BRASILEIRA DE CORREIOS E TELEGRAFOS", com um total de 7 notas.

Explicação: Para chegar a este resultado, contei o número de notas fiscais distintas (coluna "NÚMERO") agrupadas pela razão social do emitente (coluna "RAZÃO SOCIAL EMITENTE") na tabela ai_table_cabecalho e ordenei o resultado para encontrar a empresa com a maior quantidade de notas.


### 4 - Qual item de maior valor total?

Entendi que você quer saber qual é o item com o maior valor total.

Resultados: O item de maior valor total é "HGC 4 Branco/Branco-300-CP", com um valor total de R$ 985050.00.

Explicação: Para chegar a este resultado, agrupei os itens pela coluna "DESCRIÇÃO DO PRODUTO/SERVIÇO" e somei a coluna "VALOR TOTAL" para cada item, ordenando do maior para o menor e limitando o resultado ao primeiro item.


### 5 - (Desafio) Qual nota fiscal com maior número de itens distintos? Qual valor total dessa nota? Qual item de maior valor total dessa nota? Qual porcentagem o item de maior valor representa nessa nota?

Análise: Entendi que você deseja saber qual é a nota fiscal com o maior número de itens distintos, o valor total dessa nota, qual o item de maior valor total nessa nota e qual a porcentagem que esse item representa no valor total da nota.  

Resultados:  
A nota fiscal com o maior número de itens distintos é a de número 368082, com 51 itens diferentes.  
O valor total da nota fiscal é de R$ 274,56.  
O item de maior valor total nessa nota é `"2023-O GATO VIU-2020"`, com um valor de **R$ 9,10**.  
Este item representa 3,31% do valor total da nota fiscal.  
Explicação: Para chegar a este resultado, primeiramente identifiquei a nota fiscal com o maior número de itens distintos, contando os itens únicos na tabela `ai_table_itens` agrupados pelo número da nota fiscal. Em seguida, filtrei a tabela `ai_table_itens` para encontrar o item de maior valor total dentro dessa nota. Por fim, calculei a porcentagem que este item representa no valor total da nota, dividindo o valor do item pelo valor total da nota fiscal (obtido da tabela `ai_table_cabecalho`) e multiplicando por 100.

## 4.     Link para acessar o agente.
[AgenteFiscal-Chat](https://n8n.connorai.space/webhook/b46b73d7-b028-4f31-83de-ff97d29fdbe8/chat)
