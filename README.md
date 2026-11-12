# SAR — análise de imagens de satélite

Notebook exploratório para análise de imagens Sentinel na região de Cheia Estrela e no porto de Rio Grande (RS), usando Google Earth Engine, Sentinel-1 e Sentinel-2.

## O que o notebook faz

- Compara imagens Sentinel-1 de períodos antes e durante um evento na região de Cheia Estrela.
- Explora a detecção de alvos brilhantes em imagens SAR e máscaras de água e estruturas fixas no porto de Rio Grande.
- Agrupa pixels de imagens Sentinel-2 com K-means, incluindo uma análise restrita a áreas classificadas como terra pelo MNDWI.
- Aplica um detector CFAR simplificado a uma cena Sentinel-1, agrupa pixels candidatos e calcula medidas como área, intensidade, contraste, alongamento e coordenadas.
- Demonstra uma classificação exploratória dos candidatos com Random Forest após a rotulagem manual dos exemplos.

> As detecções são candidatas geradas por regras e limiares experimentais; não representam uma classificação validada de embarcações ou uma ferramenta operacional.

## Requisitos

- Python 3.12 (o notebook está configurado para o kernel `Python (SAR)`).
- Conta Google com acesso ao Google Earth Engine.
- Projeto Google Cloud habilitado para Earth Engine e acesso ao projeto configurado no notebook.

Instale as dependências em um ambiente virtual:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install earthengine-api geemap numpy pandas scipy matplotlib scikit-learn ipykernel
```

Configure a autenticação e o projeto do Earth Engine:

```powershell
earthengine authenticate
```

O notebook inicializa o Earth Engine com o projeto `projeto-estrela-513916`. Troque esse identificador pelo projeto ao qual sua conta tem acesso, se necessário.

## Como executar

1. Abra `cheia_estrela.ipynb` no VS Code ou Jupyter.
2. Selecione o kernel do ambiente em que instalou as dependências.
3. Autentique o Earth Engine e confirme o projeto configurado.
4. Execute as células de cima para baixo: elas compartilham variáveis e resultados.

As datas, coordenadas, limites de nuvem e parâmetros de detecção estão nas próprias células e podem ser ajustados para outros períodos ou áreas. A exportação e o treinamento de classificadores dependem das configurações e dos dados usados na execução.

## Fontes de dados

- `COPERNICUS/S1_GRD` — imagens Sentinel-1 SAR.
- `COPERNICUS/S2_SR_HARMONIZED` — reflectância de superfície Sentinel-2.

Ambas as coleções são acessadas pelo Google Earth Engine; os dados não são armazenados neste repositório.
