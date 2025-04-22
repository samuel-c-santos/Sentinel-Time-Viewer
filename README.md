# Sentinel-Time-Viewer
🛰️ Comparação temporal de imagens Sentinel‑2 com controle deslizante (swipe) e sobreposição vetorial usando Google Earth Engine e geemap.

## ✨ Visão Geral

Este notebook implementa uma interface interativa para visualização e comparação temporal de imagens Sentinel‑2, usando Google Earth Engine (GEE) e a biblioteca geemap no Google Colab. A aplicação permite comparar dois anos distintos com controle deslizante (swipe) e exibe um contorno vetorial da área de interesse por cima das imagens.

## 📂 Funcionalidades

- Upload de shapefile (.zip) diretamente no Colab;
- Filtragem automática de imagens Sentinel‑2 com menos de 10% de nuvens;
- Seleção e visualização de imagens por ano;
- Swipe interativo para comparação entre anos;
- Contorno do polígono vetorial visível em todas as camadas.

## 🛰️ Dados Utilizados

- [Sentinel‑2 Surface Reflectance](https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR)
  - Coleção: `COPERNICUS/S2_SR`
  - Bandas: `B4 (Red), B3 (Green), B2 (Blue)`

## 📌 Requisitos

- Conta Google Earth Engine
- Google Colab
- Bibliotecas:
  - `earthengine-api`
  - `geemap`
  - `ipywidgets`

## ▶️ Como Usar

1. Acesse o notebook hospedado neste repositório e execute diretamente no Google Colab clicando [aqui](https://github.com/samuel-c-santos/Sentinel-Time-Viewer/blob/main/GEE_swipe.ipynb).
2. Faça upload de um shapefile compactado (.zip).
3. A aplicação centraliza o mapa e apresenta o controle deslizante.
4. Escolha os anos desejados para visualização.
5. O contorno vetorial do polígono será exibido por cima das imagens.

## 💡 Possíveis Extensões

- Inclusão de sensores Landsat (LC08, LC09, etc.);
- Adição de índices espectrais (NDVI, NBR);
- Exportação de imagens processadas;
- Comparação por semestre ou por estação do ano.

## 📷 Exemplo

![exemplo_swipe](exemplo_swipe.gif)

## 👨‍💻 Autor

Samuel da Costa dos Santos  
Especialista em Geoprocessamento | Regularização Ambiental | GEE & Python

