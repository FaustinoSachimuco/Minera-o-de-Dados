# UNIVERSIDADE DO MINHO - UMINHO
## Mineração de Dados
**Alunos:**
- *PG50944 Fautisno Sachimuco - MMC*
- *PG50008 Marcos André Mussungo - MEI*
- *PG52762 Lívia Péres Bettero - MHD*


# Tema: Modelo Baseado em LLM para Discutir o Programa Eleitoral do Partido AD (Aliança Democrática)

## Objectivo Geral
Desenvolver e avaliar um modelo baseado em Linguagem Natural (LLM) para discutir com o usuário o as propostas de governo do Partido Aliança Democrática, com base em seu Programa Eleitoral apresentado nas eleições de 2024 - conteúdo do site oficial, vídeos do canal oficial e reportagens de sites confiáveis - de forma ética.

## Fonte de Dados
A fonte de dados para este projeto foi constituída a partir das seguintes fontes:
  . Programa Eleitoral em PDF
  . Web Scrapping de conteúdo do site oficial
  . Web Scrapping de conteúdo de publicações em sites de notícias considerados confiáveis:

## Metodologia
### Scrapping de Dados
#### Fontes de Dados, Bibliotecas e Ferramentas
   Foram selecionados como fontes de dados os seguintes:
   ##### Site oficial do partido Aliança Democrática, considerando textos do site e outros arquivos como o pdf com o proposta de governo
   Foi utilizado o wget para baixar e analisar o que se podia extrair do site inicialmnete. Como comando, foi baixado o arquivo PDF da proposta de governo e algumas poucas páginas em formato html.
   A extração dos textos do arquivo PDF contendo a proposta de governo do AD foi feita dentro da função *pdf_scrapping()* do código em python, com a biblioteca **PyPDF2** (https://pypi.org/project/pypdf/#description). Foram removidos caracteres como "• " e quebras de linha no meio de frases.
   Já os textos em formato html do site, que incluíam hino, textos de apoio e notícias, foram extraídos na função *extrai_oficial()* usando as bibliotecas **jjcli** (https://pypi.org/project/jjcli/) e **BeautifulSoup** (https://pypi.org/project/beautifulsoup4/).
      
   ##### Sites de notícias de grandes veículos, considerados confiáveis.
   Foi criada uma lista de sites indicados para extração dos arquivos. As noticias selecionadas passaram por análise humana devido á preocupação com questões éticas que envolvem o tipo de chatbot que seria treinado.
   ![image](https://github.com/FaustinoSachimuco/chatBot_Alinca_Democratica/assets/121136618/0f260690-def6-4b15-8845-3566e3f83e5f)


   O código para extração dos textos seguiu o modelo do primeiro código utilizado no site oficial, mas por se tratar de sites com estruturas difertenes, foi necessário criar um segundo arquivo contendo a referência de que tags deveriam ser extraídas e que tags deveriam ser desconsideradas pelo script.
   Os textos passaram também por uma limpeza para remoção de linhas em branco e caracteres especiais e pequenos blocos de texto indesejados como "Leia Mais", "&quot" e outros.   

   ##### Vídeos oficiais do partido disponíveis no canal do Youtube
   Para os vídeos oficiais disponíveis no youtube, inicialmente cogitou-se fazer download dos audios dos videos com a API do Youtube, seguida da transcrição com a API do Speech to Text do Google, mas ao final, a ferramenta Download Youtube Subtitles (https://www.downloadyoutubesubtitles.com/) resultou mais ágil para o volume de textos que se precisava baixar.
   Os textos foram gravados em arquivos individuais e postos em uma pasta para tratamento via script onde foram remividas quebras de linhas.
Ao fim do scarapping, os textos extraídos foram gravados no mesmo arquiv, "SAIDA.txt"

Mesmo nos textos extraídos de sites confiáveis e de publições oficiais do partido AD, ainda foi possível identificar partes de discursos que precisariam ser filtradas por questões éticas, principalmente nas transcrições de vídeos de candidatos do AD no youtube, tais como:
-*"Eu sei que o líder do PS adora automóveis de luxo – agora parece que os esconde (...)"*
-*"(...) comparar o doutor Nuno Santos com o professor Cavaco Silva é comparar um Ferrari com um calhambeque encostado numa garagem (...)"*
-*"(...) o partido socialista e Pedro Nuno Santos que enquanto Ministro mostrou tudo menos preparação."*
-*"Torna-se vital inverter uma gestão socialista caótica (...)"*
-*"(...) a experiência do líder do Partido Socialista está marcada por exemplos dessa cultura de informalidade (...)"*

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
          novo - reportagem - https://www.cnnbrasil.com.br/internacional/alianca-democratica-deve-vencer-eleicoes-legislativas-aponta-projecao-da-cnn/
          novo - reportagem - https://www.cnnbrasil.com.br/internacional/governo-minoritario-de-centro-direita-assume-em-portugal-nesta-terca-feira-2/
          novo - reportagem - https://www.cnnbrasil.com.br/internacional/portugal-tem-instabilidade-e-confronto-com-extrema-direita-em-votacao-para-presidente-do-parlamento/
          novo - reportagem - https://www.cnnbrasil.com.br/internacional/alianca-vencedora-das-eleicoes-em-portugal-tenta-contornar-extrema-direita-com-gastos/
          novo - reportagem - https://www.cnnbrasil.com.br/internacional/chega-nao-ganhou-as-eleicoes-em-portugal-mas-e-o-maior-vitorioso-da-noite/
          novo - reportagem - https://www.cnnbrasil.com.br/internacional/portugal-vai-as-urnas-em-eleicao-que-ocorre-dois-anos-antes-do-previsto/
          novo - reportagem - https://rr.sapo.pt/noticia/politica/2024/02/13/alianca-democratica-apresenta-programa-eleitoral-queremos-virar-a-pagina-do-desespero/366201/
          novo - reportagem - https://www.voaportugues.com/a/portugal-l%C3%ADder-da-alian%C3%A7a-democr%C3%A1tica-sem-maioria-assume-que-far%C3%A1-governo/7522196.html
          novo - reportagem - https://www.rfi.fr/pt/mundo/20240311-alian%C3%A7a-democr%C3%A1tica-ganha-por-pouco-e-chega-consegue-eleger-48-deputados
          novo - reportagem - https://www.dn.pt/3040673111/projecoes-dao-vitoria-a-alianca-democratica-e-grande-crescimento-do-chega/
          novo - reportagem - https://www.rtp.pt/noticias/politica/alianca-democratica-em-busca-de-uma-efetiva-mudanca-politica_es1552304
          novo - reportagem - https://observador.pt/2024/02/05/alianca-democratica-vence-mas-fica-a-tres-deputados-da-maioria/
          novo - reportagem - https://www.publico.pt/2024/01/06/politica/noticia/alianca-democratica-propoe-governo-maioritario-condena-radicalismo-ideologico-2075938
          novo - reportagem - https://sicnoticias.pt/pais/2024-01-10-Alianca-Democratica-2.0-reescrever-o-passado-e-eclipsar-o-presente-7e81edb2
          novo - reportagem - https://eco.sapo.pt/2023/12/21/psd-e-cds-anunciam-coligacao-alianca-democratica/
          novo - reportagem - https://eco.sapo.pt/2024/02/09/alianca-democratica-ja-divulgou-programa-eleitoral-com-mote-mudanca-segura-leia-aqui/
          novo - reportagem - https://visao.pt/atualidade/politica/2023-12-15-ad-3-0-as-historias-e-memorias-da-alianca-democratica-que-juntou-os-aliados-mais-fiaveis/
          novo - reportagem - https://visao.pt/atualidade/politica/2024-03-08-alianca-democratica-faz-o-ultimo-apelo-ao-voto-util-e-aos-indecisos/
          novo - reportagem - https://visao.pt/atualidade/politica/2024-01-06-eleicoes-acordo-da-ad-destaca-experiencia-de-governo-e-alerta-para-afinidade-do-ps-com-esquerda-radical/
          novo - reportagem - https://visao.pt/atualidade/politica/2023-12-21-e-oficial-vem-ai-uma-nova-ad/
          novo - reportagem - https://capmagellan.com/carlos-goncalves-alianca-democratica/
          novo - reportagem - https://www.poder360.com.br/internacional/alianca-de-centro-direita-diz-ter-vencido-eleicao-em-portugal/
          novo - reportagem - https://g1.globo.com/mundo/noticia/2024/03/10/urnas-fecham-em-portugal-os-tres-partidos-com-mais-chances-aguardam-os-resultados.ghtml
          novo - reportagem - https://g1.globo.com/mundo/blog/sandra-cohen/post/2024/03/11/terceira-forca-politica-chega-impora-instabilidade-e-complicada-governabilidade-em-portugal.ghtml
          novo - reportagem - https://g1.globo.com/mundo/noticia/2024/03/28/presidente-de-portugal-aprova-ministerio-de-novo-primeiro-ministro-que-vai-governar-com-minoria-no-parlamento.ghtml
          novo - reportagem - https://eco.sapo.pt/2024/01/07/a-saude-e-a-grande-prioridade-social-do-governo-da-alianca-democatica/
          novo - reportagem - https://cnnportugal.iol.pt/eleicoes-legislativas/eleicoes/alianca-democratica-ganhou-sera-que-chega/20240311/65ee43e2d34e8d13c9b8ad76
