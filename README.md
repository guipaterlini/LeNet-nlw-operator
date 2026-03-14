# LeNet-5 com PyTorch (MNIST)

Projeto didático com implementação da arquitetura LeNet-5 em PyTorch, treinamento no MNIST, avaliação, análise de erros e visualização de ativações no notebook `lenet5.ipynb`.

## Objetivo

Este projeto foi organizado para facilitar estudo e experimentação de CNNs clássicas.  
No notebook você encontra, em ordem:

1. Definição da arquitetura LeNet-5  
2. Instanciação do modelo  
3. Visualização de filtros iniciais  
4. Carregamento e visualização do MNIST  
5. Treinamento  
6. Avaliação no teste  
7. Análise de erros (amostras classificadas incorretamente)  
8. Visualização da saída da primeira camada convolucional  
9. Salvamento do modelo  
10. Carregamento do checkpoint salvo

## Tecnologias

- Python 3.12+
- PyTorch
- Torchvision
- Matplotlib
- UV (gerenciador de ambiente/dependências)
- Jupyter/IPython Kernel

## Estrutura do Projeto

```
lenet/
├── lenet5.ipynb
├── pyproject.toml
├── uv.lock
├── checkpoints/              # gerado ao salvar o modelo
│   └── lenet5_mnist.pth
└── data/
    └── MNIST/
        └── raw/              # arquivos do dataset
```

## Pré-requisitos

- Ter `uv` instalado: [https://docs.astral.sh/uv/](https://docs.astral.sh/uv/)
- Python compatível com o projeto (`>=3.12`)

## Setup do Ambiente

No diretório do projeto:

```bash
uv sync
```

Esse comando cria/atualiza o ambiente virtual e instala as dependências definidas em `pyproject.toml`.

## Como Executar o Notebook

1. Abra o projeto no Cursor/VS Code.
2. Abra `lenet5.ipynb`.
3. Selecione o kernel do ambiente `.venv` criado pelo `uv`.
4. Execute as células em ordem (`Run All` ou célula a célula).

## Hiperparâmetros Atuais

No notebook, o treinamento usa:

- `learning_rate = 0.001`
- `batch_size = 64`
- `num_epochs = 5`

## Treinamento e Avaliação

O fluxo principal usa:

- `CrossEntropyLoss`
- `Adam` como otimizador
- avaliação no conjunto de teste com cálculo de `Test Loss` e `Test Accuracy`

## Salvamento e Carregamento do Modelo

O notebook salva um checkpoint em:

`checkpoints/lenet5_mnist.pth`

Conteúdo salvo:

- `model_state_dict`
- `learning_rate`
- `batch_size`
- `num_epochs`

Também há célula para recarregar esse checkpoint e reconstruir o modelo para inferência.

## Troubleshooting

### Erro de download/SSL no MNIST

O notebook está configurado para usar o MNIST local com `download=False`.  
Se os arquivos não estiverem presentes em `./data`, será necessário baixar o dataset antes.

### Kernel/ambiente incorreto

Se ocorrer erro de import:

- confirme que o kernel selecionado é o da `.venv` do projeto;
- execute `uv sync` novamente.

## Próximos Passos Sugeridos

- Adicionar validação por época
- Plotar curvas de loss/accuracy (treino vs teste)
- Salvar também estado do otimizador
- Adicionar matriz de confusão
- Testar variações da arquitetura (dropout, batch norm, etc.)
