YOLOv5 com Transfer Learning
Este repositório contém o código e as configurações para aplicar Transfer Learning na rede YOLOv5 utilizando o COCO Dataset filtrado. O objetivo é treinar um modelo de detecção de objetos para duas classes específicas (person e dog), além das classes previamente treinadas.

Objetivo do Projeto
O objetivo é explorar o potencial do Transfer Learning para personalizar o YOLOv5 e adaptá-lo para tarefas específicas de detecção de objetos. Para isso:

Filtramos as imagens e anotações do COCO Dataset para incluir apenas as classes de interesse.
Utilizamos o Google Colab para configurar o ambiente e realizar o treinamento.
Avaliamos o desempenho do modelo nas novas classes treinadas.
Pré-requisitos
Para reproduzir este projeto, você precisará:

Conta no Google Colab.
Dataset COCO (disponível aqui).
Familiaridade com Python e PyTorch.
Biblioteca YOLOv5 clonada do repositório oficial.
Como Reproduzir
1. Configurar o Ambiente no Colab
Clone este repositório no Colab e instale as dependências:
bash
Copiar
Editar
!git clone https://github.com/SEU_USUARIO/YOLOv5-Transfer-Learning.git
%cd YOLOv5-Transfer-Learning
!pip install -r requirements.txt
2. Baixar e Filtrar o COCO Dataset
Use o script para filtrar as classes person e dog:
bash
Copiar
Editar
python scripts/filter_coco.py
3. Configurar os Dados
Ajuste o arquivo coco_filtered.yaml para apontar para os diretórios de treinamento e validação.
4. Treinar o Modelo
Execute o treinamento com o comando:
bash
Copiar
Editar
python train.py --img 640 --batch 16 --epochs 50 --data coco_filtered.yaml --weights yolov5s.pt
5. Testar o Modelo
Para testar o modelo treinado:
bash
Copiar
Editar
python detect.py --weights runs/train/exp/weights/best.pt --img 640 --source data/val
Estrutura do Repositório
bash
Copiar
Editar
YOLOv5-Transfer-Learning/
├── coco_filtered.yaml       # Configuração do dataset
├── scripts/
│   ├── filter_coco.py       # Script para filtrar classes do COCO
├── yolov5/                  # Repositório YOLOv5
├── requirements.txt         # Dependências do projeto
├── README.md                # Documentação
