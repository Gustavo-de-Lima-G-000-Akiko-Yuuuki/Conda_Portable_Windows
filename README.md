# 📦 Miniconda Portátil – Guia Completo de Instalação e Uso

Este é o manual oficial do projeto **Swift_AI**.

Este guia detalhado ensina qualquer usuário a instalar, configurar e utilizar o **Miniconda 3 Portátil**, criar ambientes Python isolados e rodar a aplicação **YOLO / Swift_AI** através do script interativo `Gerenciador YOLO`.

> **Vantagem da Portabilidade:**
> O procedimento não instala nada no Windows, não escreve registro e não altera o `PATH`. Toda a estrutura fica **100% dentro da pasta do projeto** — completamente portátil.

## 📁 Estrutura Final do Projeto

A estrutura de diretórios final do projeto deve ser a seguinte:

```
C:\Projeto Swift_AI\
│
├── Miniconda3_portable\
│   ├── envs\
│   │   └── esteira_env\
│   │        └── python.exe
│   └── ...
│
├── app.py
├── requirements.txt
├── gerenciador_yolo.bat
└── README.md
```

## 1️⃣ Download do Miniconda Portátil

O Miniconda não possui uma versão ZIP oficial, mas pode ser instalado em modo portátil.

**Download Oficial:**

Acesse a página oficial da Anaconda/Miniconda:
[https://docs.anaconda.com/miniconda](https://docs.anaconda.com/miniconda)

Baixe o instalador para Windows de 64 bits:
`Miniconda3-latest-Windows-x86_64.exe`

## 2️⃣ Instalação Portátil (sem mexer no sistema)

1.  Crie a pasta base do projeto:
    ```
    C:\Projeto Swift_AI
    ```
2.  Coloque o instalador do Miniconda (`Miniconda3-latest-Windows-x86_64.exe`) dentro dessa pasta.
3.  Abra o **CMD** (Prompt de Comando) nessa pasta e execute o comando de instalação silenciosa e portátil:

    ```bash
    Miniconda3-latest-Windows-x86_64.exe ^
      /InstallationType=JustMe ^
      /AddToPath=0 ^
      /RegisterPython=0 ^
      /NoRegistry=1 ^
      /S ^
      /D=C:\Projeto Swift_AI\Miniconda3_portable
    ```

| Parâmetro | Efeito |
| :--- | :--- |
| `/AddToPath=0` | ✔ Não altera o `PATH` do sistema. |
| `/RegisterPython=0` | ✔ Não registra o Python no sistema. |
| `/NoRegistry=1` | ✔ Não cria ícones ou entradas no registro. |
| `/D=...` | ✔ Instala tudo local, garantindo a portabilidade. |

## 3️⃣ Criar o Ambiente Python Portátil

Após a instalação, crie o ambiente Python isolado:

1.  Navegue até a pasta de instalação do Miniconda:
    ```bash
    cd C:\Projeto Swift_AI\Miniconda3_portable
    ```
2.  Crie o ambiente `esteira_env` dentro da pasta correta:
    ```bash
    condabin\conda.bat create -p "%cd%\envs\esteira_env" python=3.11 -y
    ```

O Python portátil do projeto estará localizado em:
`C:\Projeto Swift_AI\Miniconda3_portable\envs\esteira_env\python.exe`

## 4️⃣ Instalar Dependências (YOLO, OpenCV, Torch etc.)

Instale as bibliotecas necessárias listadas no arquivo `requirements.txt`:

1.  Navegue até a pasta raiz do projeto:
    ```bash
    cd C:\Projeto Swift_AI
    ```
2.  Execute a instalação usando o Python do ambiente portátil:
    ```bash
    Miniconda3_portable\envs\esteira_env\python.exe -m pip install -r requirements.txt
    ```

**Alternativa (Instalação Manual):**

Se preferir instalar manualmente as dependências principais:
```bash
python -m pip install opencv-python ultralytics torch numpy pillow
```

## 5️⃣ Usando o Script Interativo (`Gerenciador YOLO`)

O arquivo `gerenciador_yolo.bat` facilita a execução e o gerenciamento para o usuário final.

**Funções do Menu:**

*   Executar o app YOLO (`app.py`)
*   Abrir terminal Python
*   Instalar dependências (`requirements.txt`)
*   Listar pacotes instalados
*   Sair

**Como usar:**

Basta clicar duas vezes no arquivo:
```
gerenciador_yolo.bat
```

## 6️⃣ Como Funciona o `Gerenciador YOLO`

O script `gerenciador_yolo.bat` detecta automaticamente os caminhos necessários:

*   Pasta do projeto
*   Pasta do Miniconda portátil
*   Ambiente `esteira_env`
*   Python portátil

Ele **nunca** usa o Python do sistema, apenas o Python interno do ambiente isolado:
`C:\Projeto Swift_AI\Miniconda3_portable\envs\esteira_env\python.exe`

## 7️⃣ Ativar Ambiente Manualmente (Opcional)

Se for necessário ativar o ambiente via terminal para depuração ou uso avançado:

1.  Navegue até a pasta de instalação do Miniconda:
    ```bash
    cd C:\Projeto Swift_AI\Miniconda3_portable
    ```
2.  Ative o ambiente:
    ```bash
    condabin\conda.bat activate "%cd%\envs\esteira_env"
    ```
3.  Após a ativação, você pode executar o aplicativo:
    ```bash
    python app.py
    ```

## 8️⃣ Tornar o Projeto 100% Portátil (ZIP)

Para enviar o projeto a outra pessoa ou fazer um backup completo:

1.  Feche todos os terminais e processos relacionados ao projeto.
2.  Compacte a pasta inteira `C:\Projeto Swift_AI` em um arquivo ZIP.
3.  Envie o arquivo ZIP.

No outro PC, basta extrair o ZIP para que o projeto funcione imediatamente:

*   ✔ Não precisa instalar Python
*   ✔ Não precisa instalar Miniconda
*   ✔ Não mexe no Windows
*   ✔ Funciona imediatamente

## 9️⃣ Erros Comuns e Soluções

| Erro Comum | Solução |
| :--- | :--- |
| **Python não encontrado** | O ambiente não existe. Crie-o novamente navegando para `C:\Projeto Swift_AI\Miniconda3_portable` e executando: `condabin\conda.bat create -p "%cd%\envs\esteira_env" python=3.11 -y` |
| **Pip não instala** | Certifique-se de executar o `pip` com o Python correto do ambiente: `Miniconda3_portable\envs\esteira_env\python.exe -m pip install -r requirements.txt` |
| **Conda errado está sendo usado** | Sempre use o executável específico: `condabin\conda.bat`. Nunca use `_conda` ou `conda` sozinho. |

## 🔟 Créditos

Este manual foi criado para facilitar a instalação e uso de ambientes portáteis no projeto **Swift_AI**, garantindo isolamento, portabilidade e facilidade para qualquer tipo de usuário, mesmo sem conhecimento técnico.
