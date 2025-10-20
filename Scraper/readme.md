
# Crawler de Notícias dos Municípios Baianos

Script automatizado para monitoramento de notícias relacionadas a corrupção, fraudes, operações policiais e irregularidades em municípios da Bahia através do Google News. Desenvolvido para apoiar o trabalho de análise do Tribunal de Contas dos Municípios da Bahia (TCM-BA).

## Descrição

Este script realiza buscas automatizadas no Google News sobre diversos temas relacionados a irregularidades administrativas e operações policiais nos municípios da Bahia. Ele utiliza:

- Selenium para automação do navegador
- BeautifulSoup para extração dos dados
- Processamento de linguagem natural para identificação de municípios
- Pandas para manipulação e exportação dos dados

## Funcionalidades

- Busca automática por termos passados através de um arquivo ```.txt```
- Identificação inteligente de municípios citados nas notícias
- Tratamento de palavras ambíguas para evitar falsos positivos
- Normalização e validação de datas de publicação
- Coleta de metadados completos (título, conteúdo, fonte, data, link, imagem)
- Eliminação automática de notícias duplicadas
- Exportação organizada em Excel

## Requisitos

- Python 3.8+
- Google Chrome instalado
- ChromeDriver compatível com sua versão do Chrome
- Pacotes Python listados em requirements.txt

Obs.: Para instalar o ChromeDriver, baixe a versão compatível com seu Chrome [aqui](https://developer.chrome.com/docs/chromedriver/get-started?hl=pt-br#setup) e adicione ao PATH do sistema ou coloque no diretório do script.

## Instalação

```
pip install -r requirements.txt
```

```
python -m spacy download pt_core_news_lg (ou pt_core_news_sm para um tamanho menor)
```

## Como usar

1. Certifique-se de que o ChromeDriver está configurado corretamente
2. Execute o script principal:

```
python .\src\main.py -t <caminho_para_arquivo_txt_com_termos_de_pesquisa> -s <nome_do_arquivo_de_saida>
```
Exemplo:
```
python .\src\main.py -t .\src\termos_pesquisa\termos_para_pesquisa.txt -s saida
```

Para mais detalhes ou ajuda utilize: ```python .\src\main.py --help```

3. O script irá:
   - Buscar notícias para múltiplos termos de pesquisa
   - Processar e identificar municípios citados
   - Coletar metadados completos
   - Salvar os resultados em `nome_arquivo_de_saida_(timestamp).xlsx`

## Saída

O arquivo `nome_arquivo_de_saida_(timestamp).xlsx` contém as seguintes informações para cada notícia:

- Título
- Conteúdo
- Municípios citados
- Fonte
- Data de publicação
- Link
- URL da imagem
- Palavra-chave utilizada na busca

## Exemplo de execução


``` 
Buscando notícias para: Desvio Milionário Bahia
Acessando: https://news.google.com/search?q=Fraude+Licitação+Bahia&hl=pt-BR&gl=BR&ceid=BR%3Apt-419
Notícias encontradas na página: 101
============================================== NOTÍCIA ===================================================
TÍTULO: Justiça Federal condena ex-prefeito de Riacho de Santana por desvio milionário do Fundeb
CONTEÚDO: Conteúdo não encontrado...
MUNICÍPIOS CITADOS (1): Riacho de Santana-2926400
FONTE: Agência Sertão
DATA: 04/09/2019
LINK: https://news.google.com/./read/CBMi1AFBVV95cUxNSGswUm9RUlRFR2Q1X0Z3bjFBalV5MVNVLXdES0tia1U4N25fMUhZOUdBRjFlclc1aDBZcnFwYzNQTEY3bEo3MV9DV181S1lxYWRFdEs0Z2MtRmNaeWtEQ3pzRnZGak1oeUl5QksxdlRNcG83Vlc1Tm0ydUN6TUdSOHFLdFdmS0lFZkl4UUswZHMxV1VPVlB0cHA0Qlh3RDUxbDhwRm5JOGRZbVVhUG9BZUQ4U2JUd29UTzBFY1UyYlI1blZwelVQalAzUjBzSTl5RUlVVtIB2gFBVV95cUxQaGdOZVRrLXJUM0V6X04taW9pTjEwbXQ3SU5OZGdCR29IS04xWUxKdFdweTFHWksyLXBwSWlxeG1ENkxOcnFTLV9TdDRzcHBpbWlOLTlrVVZuc3Z2VGh4c3lwV0VXR0xmRnBxbjhWcTVRY2JrVF9PUXNxOGVDRUpCSEtvTFAweEpXdjJ3V0UzeXlkQXp0N3V2ZkNMQTlWUUNTR1NnT2JxV2JveU9BQzduZkl3OXI5dk9hMXFHOFA2SVZaYVY0OVRFX21JMDg4ZDloTl8xV3Y0X2Rudw?hl=pt-BR&gl=BR&ceid=BR%3Apt-419
IMAGEM: https://news.google.com/api/attachments/CC8iJ0NnNTRlWEk0VDNCZk56QnBXak42VFJDa0F4amJCU2dLTWdNQmNRUQ=-w200-h112-p-df-rw
PALAVRA-CHAVE: Desvio Milionário Bahia
```

## Observações

- O script utiliza modo headless (sem interface gráfica) para melhor performance
- Inclui tratamento robusto de erros e timeouts
- Implementa scroll automático para carregar mais notícias
- Possui sistema inteligente para evitar duplicatas
- Realiza validação e normalização de dados

## Autor

Hugo Rios Brito
