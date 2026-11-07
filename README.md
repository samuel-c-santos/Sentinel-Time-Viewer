# Sentinel-Time-Viewer

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/NGEO-IDEFLOR-Bio/Sentinel-Time-Viewer/blob/main/GEE_swipe.ipynb)

Comparador temporal de imagens Sentinel-2 Surface Reflectance com controle deslizante (swipe), persistencia de limite vetorial sobreposto e modulo exportador de animacao em GIF em formato paisagem (1,91:1) via Google Earth Engine e geemap em ambiente Google Colab.

## Demonstracao

![Demonstracao do Swipe](exemplo_swipe.gif)

## Finalidade

O Sentinel-Time-Viewer executa a comparacao visual direta entre dois periodos anuais distintos dentro de um poligono delimitador. A ferramenta opera no Google Colab integrada a API do Google Earth Engine (GEE). O contorno do poligono permanece renderizado sobre as duas camadas raster do controle deslizante, mantendo a referencia espacial durante o deslocamento da barra de divisao.

## Especificacoes Tecnicas

* Colecao de imagens: `COPERNICUS/S2_SR_HARMONIZED` (Sentinel-2 Surface Reflectance com calibracao harmonizada).
* Resolucao espacial: 10 metros nas bandas do visivel.
* Composicao espectral: Bandas B4 (Vermelho), B3 (Verde) e B2 (Azul).
* Agregacao temporal: Mediana anual das cenas filtradas por cobertura de nuvens.
* Mapas base compativeis: Google Hybrid, Google Satellite, Google Roadmap e Esri World Imagery.
* Enquadramento de exportacao: Proporcao horizontal paisagem 1,91:1 (resolucoes de 1200 x 628, 960 x 502 ou 800 x 418 pixels) com margem de contexto territorial calculada automaticamente.

## Requisitos

* Conta com acesso ativo ao Google Earth Engine.
* Projeto Google Cloud com a Earth Engine API habilitada.
* Ambiente de execucao Google Colab.
* Bibliotecas Python: `earthengine-api`, `geemap`, `ipywidgets`, `pycrs`, `pillow`, `requests`.

## Estrutura do Notebook

O script interativo e organizado em seis celulas com interface grafica recolhida por padrao:

1. Instalacao de Dependencias: instala e atualiza bibliotecas necessarias.
2. Autenticacao e GCP Project ID: campo de texto para definicao do identificador de projeto Google Cloud e inicializacao da sessao.
3. Parametros de Processamento: definicao do percentual maximo de cobertura de nuvens aceito por cena, intervalo de meses para agregacao, basemap e estilizacao do contorno vetorial.
4. Definicao da Area de Interesse: upload do arquivo vetorial (formato Shapefile compactado em .zip) ou selecao de poligono demonstrativo (Parque Estadual do Utinga).
5. Visualizador Temporal (Swipe): consulta server-side no catalogo do GEE para identificar apenas os anos que possuem cenas validas no periodo e geracao da interface dividida com seletores de ano independentes e tela limpa sem sobreposicoes textuais obstrutivas.
6. Exportador de Animacao em GIF: geracao de arquivo GIF animado com efeito swipe oscilante entre dois anos escolhidos, enquadramento paisagem 1,91:1 com compensacao latitudinal e margem de contexto, delimitacao vetorial preservada e ticker horizontal institucional fixo do NGEO na borda superior.

## Instrucoes de Uso

1. Abra o notebook no Google Colab atraves do badge localizado no topo deste documento.
2. Na celula 1, execute a instalacao das dependencias.
3. Na celula 2, insira o ID do seu projeto Google Cloud no campo `GCP_PROJECT_ID` e execute a autenticacao.
4. Na celula 3, defina o limiar maximo de nuvens e o mapa base desejado.
5. Na celula 4, envie o arquivo .zip com o Shapefile contendo os arquivos .shp, .shx, .dbf e .prj.
6. Na celula 5, execute o visualizador. Os menus suspensos exibirao unicamente os anos com dados disponiveis. Mova o controle central para inspecionar a comparacao.
7. Na celula 6, informe os dois anos que deseja confrontar, selecione a resolucao horizontal desejada (padrao 1200 x 628 px) e execute a geracao do GIF animado com download automatico.

## Tratamento de Dados e Regras de Negocio

* Filtragem de Anos: O catalogo Sentinel-2 e consultado previamente para a geometria informada. Anos sem cenas que atendam ao percentual maximo de nuvens sao desconsiderados da interface, evitando o carregamento de imagens vazias.
* Resiliencia de Mapas Base: A camada base padrao utiliza Google Hybrid para evitar dependencias de servicos com autenticacao restrita ou descontinuados (como Stamen ou CARTO sem chave).
* Renderizacao Vetorial: O limite da area e convertido em camada rasterizada monocromatica e embutido no mosaico anual antes da composicao no visualizador deslizante e no exportador GIF, garantindo visibilidade continua em ambos os lados da divisao.
* Enquadramento Paisagem 1,91:1 com Contexto: A rotina de exportacao calcula uma caixa delimitadora proporcional com compensacao de projecao latitudinal e adiciona uma margem de amortecimento ajustavel (padrao 35%) em torno do poligono. Isso evita cortes abruptos nas bordas da camada e fornece a visualizacao da paisagem circundante.
* Marca D'agua Institucional Fixa: A animacao gerada inclui uma fita discreta na margem superior com deslocamento horizontal continuo (ticker) fixada com a identificacao oficial do NGEO / IDEFLOR-Bio, nao sujeita a edicoes externas.

## Autoria e Vinculacao Institucional

Nucleo de Geotecnologias (NGEO)  
Instituto de Desenvolvimento Florestal e da Biodiversidade do Estado do Para (IDEFLOR-Bio)  
Autor: Samuel da Costa dos Santos
