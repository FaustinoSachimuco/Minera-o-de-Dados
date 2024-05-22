# UNIVERSIDADE DO MINHO - UMINHO
## Mineração de Dados
**Alunos:**
- *PG50944 Fautisno Sachimuco - MMC*
- *PG50008 Marcos André Mussungo - MEI*
- *PG52762 Lívia Péres Bettero - MHD*


# Tema: Modelo Baseado em LLM para Discutir o Programa Eleitoral do Partido AD (Aliança Democrática)

## Objectivo Geral
Desenvolver um modelo baseado em Linguagem Natural (LLM) para discutir com o usuário o as propostas de governo do Partido Aliança Democrática, com base em seu Programa Eleitoral apresentado nas eleições de 2024 - conteúdo do site oficial, vídeos do canal oficial e reportagens de sites confiáveis - de forma ética.

## Fonte de Dados
A fonte de dados para este projeto foi constituída a partir das seguintes fontes:
  . Programa Eleitoral em PDF;
  . Web Scrapping de conteúdo do site oficial;
  . Web Scrapping de conteúdo de publicações em sites de notícias considerados confiáveis.

## Metodologia
### Scrapping de Dados
#### Fontes de Dados, Bibliotecas e Ferramentas
   Foram selecionados como fontes de dados os seguintes:
   ##### Site oficial do partido Aliança Democrática, considerando textos do site e outros arquivos como o pdf com o proposta de governo
   Utilisou-se o wget para baixar todo o conteúdo disponível do site, como o arquivo PDF da proposta de governo e algumas poucas páginas em formato html.
   Para extração dos textos do arquivo PDF da proposta de governo, construiu-se a função *pdf_scrapping()* em python, utilizando a biblioteca *PyPDF2* (https://pypi.org/project/pypdf/#description). Caracteres como "• " e quebras de linha no meio de frases foram removidos nesta mesma função e os texto limpo foi gravado no arquivo *TEXTO_SAIDA.txt*.
   
   O conteúdo em html do site, contando com hino, textos de apoio e notícias, foram extraídos na função *extrai_oficial()* usando as bibliotecas *jjcli* (https://pypi.org/project/jjcli/) e *BeautifulSoup* (https://pypi.org/project/beautifulsoup4/) para extração do texto dentro das tags específicas que interessavam ao projeto. O texto extraído de cada página foi adicionado ao arquivo *TEXTO_SAIDA.txt*.
         
   ##### Sites de notícias de grandes veículos, considerados confiáveis.
   Desde o princípio do projeto, houve uma preocupação com a seleção das fontes de conteúdo a fim de evitar recolher material distorcido ou irreal de sites pouco confiáveis. Por isto, optou-se por criar uma lista de sites indicados para extração dos textos, cujas selecionadas passaram por análise humana.
   Mesmo com a seleção, entendeu-se necessário criar um código que ajudasse a identificar falas antiéticas que precisassem ser filtradas devido ao tema político do chatbot a ser treinado.
   ![image: Exermplos de discursos eticamente inapropriados encontrados no texto](https://github.com/FaustinoSachimuco/chatBot_Alinca_Democratica/assets/121136618/0f260690-def6-4b15-8845-3566e3f83e5f)

   O código para extração dos textos seguiu o modelo do primeiro código utilizado no site oficial, mas por se tratar de sites com estruturas difertenes, foi necessário criar um segundo arquivo contendo a referência de que tags deveriam ser extraídas e que tags deveriam ser desconsideradas pelo script.
   Os textos passaram também por uma limpeza para remoção de linhas em branco e caracteres especiais e pequenos blocos de texto indesejados como "Leia Mais", "&quot" e outros.   

   ##### Vídeos oficiais do partido disponíveis no canal do Youtube
   Para os vídeos oficiais disponíveis no youtube, inicialmente cogitou-se fazer download dos audios dos videos com a API do Youtube, seguida da transcrição com a API do Speech to Text do Google, mas ao final, a ferramenta Download Youtube Subtitles (https://www.downloadyoutubesubtitles.com/) resultou mais ágil para o volume de textos que se precisava baixar.
   Os textos foram gravados em arquivos individuais e postos em uma pasta para tratamento via script onde foram remividas quebras de linhas.
Ao fim do scarapping, os textos extraídos foram gravados no mesmo arquiv, "SAIDA.txt"

Mesmo nos textos extraídos de sites confiáveis e de publições oficiais do partido AD, ainda foi possível identificar partes de discursos que precisariam ser filtradas por questões éticas, principalmente nas transcrições de vídeos de candidatos do AD no youtube, tais como:
- *"Eu sei que o líder do PS adora automóveis de luxo – agora parece que os esconde (...)"*
- *"(...) comparar o doutor Nuno Santos com o professor Cavaco Silva é comparar um Ferrari com um calhambeque encostado numa garagem (...)"*
- *"(...) o partido socialista e Pedro Nuno Santos que enquanto Ministro mostrou tudo menos preparação."*
- *"Torna-se vital inverter uma gestão socialista caótica (...)"*
- *"(...) a experiência do líder do Partido Socialista está marcada por exemplos dessa cultura de informalidade (...)"*

##### NLTK (Natural Language Toolkit):
pela análise de sentimentos, tokenização e sinalização da polaridade de palavras, auxilia na identificação de linguagem negativa em textos, que pode estar associada a discursos de ódio, assédio ou discriminatórios, embora não seja uma regra. Algumas frases antiéticas podem ter valor positivo enquanto outras, com valores negativos podem não infringir a ética.

##### Spacy (Industrial-Strength Natural Language Processing):
para lematização de palavras, o que auxilia na verificação de ocorrências de determinados termos considerados potencialmente antiéticos em um texto.

### Tokenização
#### ...

#### ...

### Embeddinging
#### ...

#### ...

### Construção da Interface

### Testes e Validação


# Futuros Desafios


# Conclusões





## Referências Bibliográficas##
          https://ad2024.pt
          https://ad2024.pt/pdf/ad-programa-eleitoral.pdf
          https://www.nltk.org/
          https://spacy.io/
Para converter a lista de sites em referências bibliográficas no estilo ABNT (Associação Brasileira de Normas Técnicas), siga o formato específico para referências de sites e artigos online. Aqui está como ficaria a conversão das informações fornecidas:


CAP MAGELLAN. Carlos Gonçalves Aliança Democrática. Disponível em: <https://capmagellan.com/carlos-goncalves-alianca-democratica/>. Acesso em: 21 maio 2024.

CNN BRASIL. Aliança Democrática deve vencer eleições legislativas, aponta projeção da CNN. Disponível em: <https://www.cnnbrasil.com.br/internacional/alianca-democratica-deve-vencer-eleicoes-legislativas-aponta-projecao-da-cnn/>. Acesso em: 21 maio 2024.

_____. Governo minoritário de centro-direita assume em Portugal nesta terça-feira (2). Disponível em: <https://www.cnnbrasil.com.br/internacional/governo-minoritario-de-centro-direita-assume-em-portugal-nesta-terca-feira-2/>. Acesso em: 21 maio 2024.

_____. Portugal tem instabilidade e confronto com extrema direita em votação para presidente do parlamento. Disponível em: <https://www.cnnbrasil.com.br/internacional/portugal-tem-instabilidade-e-confronto-com-extrema-direita-em-votacao-para-presidente-do-parlamento/>. Acesso em: 21 maio 2024.

_____. Aliança vencedora das eleições em Portugal tenta contornar extrema direita com gastos. Disponível em: <https://www.cnnbrasil.com.br/internacional/alianca-vencedora-das-eleicoes-em-portugal-tenta-contornar-extrema-direita-com-gastos/>. Acesso em: 21 maio 2024.

_____. Chega não ganhou as eleições em Portugal, mas é o maior vitorioso da noite. Disponível em: <https://www.cnnbrasil.com.br/internacional/chega-nao-ganhou-as-eleicoes-em-portugal-mas-e-o-maior-vitorioso-da-noite/>. Acesso em: 21 maio 2024.

_____. Portugal vai às urnas em eleição que ocorre dois anos antes do previsto. Disponível em: <https://www.cnnbrasil.com.br/internacional/portugal-vai-as-urnas-em-eleicao-que-ocorre-dois-anos-antes-do-previsto/>. Acesso em: 21 maio 2024.

DIÁRIO DE NOTÍCIAS. Projeções dão vitória à Aliança Democrática e grande crescimento do Chega. Disponível em: <https://www.dn.pt/3040673111/projecoes-dao-vitoria-a-alianca-democratica-e-grande-crescimento-do-chega/>. Acesso em: 21 maio 2024.

ECO. PSD e CDS anunciam coligação Aliança Democrática. Disponível em: <https://eco.sapo.pt/2023/12/21/psd-e-cds-anunciam-coligacao-alianca-democratica/>. Acesso em: 21 maio 2024.

 _____. Aliança Democrática já divulgou programa eleitoral com mote "Mudança Segura". Disponível em: <https://eco.sapo.pt/2024/02/09/alianca-democratica-ja-divulgou-programa-eleitoral-com-mote-mudanca-segura-leia-aqui/>. Acesso em: 21 maio 2024.

_____. A saúde é a grande prioridade social do governo da Aliança Democrática. Disponível em: <https://eco.sapo.pt/2024/01/07/a-saude-e-a-grande-prioridade-social-do-governo-da-alianca-democatica/>. Acesso em: 21 maio 2024.

G1. Urnas fecham em Portugal; os três partidos com mais chances aguardam os resultados. Disponível em: <https://g1.globo.com/mundo/noticia/2024/03/10/urnas

OBSERVADOR. Aliança Democrática vence mas fica a três deputados da maioria. Disponível em: <https://observador.pt/2024/02/05/alianca-democratica-vence-mas-fica-a-tres-deputados-da-maioria/>. Acesso em: 21 maio 2024.

PODER360. Aliança de centro-direita diz ter vencido eleição em Portugal. Disponível em: <https://www.poder360.com.br/internacional/alianca-de-centro-direita-diz-ter-vencido-eleicao-em-portugal/>. Acesso em: 21 maio 2024.

PÚBLICO. Aliança Democrática propõe governo maioritário, condena radicalismo ideológico. Disponível em: <https://www.publico.pt/2024/01/06/politica/noticia/alianca-democratica-propoe-governo-maioritario-condena-radicalismo-ideologico-2075938>. Acesso em: 21 maio 2024.

RÁDIO FRANÇA INTERNACIONAL. Aliança Democrática ganha por pouco e Chega consegue eleger 48 deputados. Disponível em: <https://www.rfi.fr/pt/mundo/20240311-alianca-democratica-ganha-por-pouco-e-chega-consegue-eleger-48-deputados>. Acesso em: 21 maio 2024.

RÁDIO RENASCENÇA. Aliança Democrática apresenta programa eleitoral: "Queremos virar a página do desespero". Disponível em: <https://rr.sapo.pt/noticia/politica/2024/02/13/alianca-democratica-apresenta-programa-eleitoral-queremos-virar-a-pagina-do-desespero/366201/>. Acesso em: 21 maio 2024.

RTP. Aliança Democrática em busca de uma efetiva mudança política. Disponível em: <https://www.rtp.pt/noticias/politica/alianca-democratica-em-busca-de-uma-efetiva-mudanca-politica_es1552304>. Acesso em: 21 maio 2024.

SIC NOTÍCIAS. Aliança Democrática 2.0: reescrever o passado e eclipsar o presente. Disponível em: <https://sicnoticias.pt/pais/2024-01-10-Alianca-Democratica-2.0-reescrever-o-passado-e-eclipsar-o-presente-7e81edb2>. Acesso em: 21 maio 2024.

VISÃO. AD 3.0: as histórias e memórias da Aliança Democrática que juntou os aliados mais fiáveis. Disponível em: <https://visao.pt/atualidade/politica/2023-12-15-ad-3-0-as-historias-e-memorias-da-alianca-democratica-que-juntou-os-aliados-mais-fiaveis/>. Acesso em: 21 maio 2024.

 _____. Aliança Democrática faz o último apelo ao voto útil e aos indecisos. Disponível em: <https://visao.pt/atualidade/politica/2024-03-08-alianca-democratica-faz-o-ultimo-apelo-ao-voto-util-e-aos-indecisos/>. Acesso em: 21 maio 2024.
 
_____. Eleições: Acordo da AD destaca experiência de governo e alerta para afinidade do PS com esquerda radical. Disponível em: <https://visao.pt/atualidade/politica/2024-01-06-eleicoes-acordo-da-ad-destaca-experiencia-de-governo-e-alerta-para-afinidade-do-ps-com-esquerda-radical/>. Acesso em: 21 maio 2024.

_____. É oficial: vem aí uma nova AD. Disponível em: <https://visao.pt/atualidade/politica/2023-12-21-e-oficial-vem-ai-uma-nova-ad/>. Acesso em: 21 maio 2024.

VOZ DA AMÉRICA. Portugal: Líder da Aliança Democrática sem maioria assume que fará governo. Disponível em: <https://www.voaportugues.com/a/portugal-l%C3%ADder-da-alian%C3%A7a-democr%C3%A1tica-sem-maioria-assume-que-far%C3%A1-governo/7522196.html>. Acesso em: 21 maio 2024.
