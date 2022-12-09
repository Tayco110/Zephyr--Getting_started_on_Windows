
# Zephyr - Getting started on Windows

## Sistema Operacional

Garanta que seu Sistema Operacional esteja atualizado.

```
Iniciar -> Configurações -> Windows Update -> Verificar se há atualizações.
Instale qualquer atualização obrigatória que esteja disponível.
```

> **_NOTA:_**  Devido a problemas para encontrar executáveis, o Projeto Zephyr atualmente não oferece suporte a *flashing* de aplicativos usando o Windows Subsystem for Linux ([WSL](https://learn.microsoft.com/en-us/windows/wsl/about)). Portanto, não recomendamos o uso do [WSL](https://learn.microsoft.com/en-us/windows/wsl/about) ao começar.

## Instalando depêndencias

| Ferramenta | Versão mínima |
| :------: | :------: |
| [CMake](https://cmake.org/) | 3.20.0 |
| [Python](https://www.python.org/) | 3.8.0 |
| [Chocolatey](https://chocolatey.org/install) | --- |

As instruções apresentadas baixo devem ser executadas no `cmd.exe` do Windows em sua versão de administrador.

1. Instale o [CMake](https://cmake.org/).
2. Instale o [Python](https://www.python.org/).
3. Instale o [Chocolatey](https://chocolatey.org/install).

* Abra o `cmd.exe`.
* Desative a confirmação global para evitar ter que confirmar a instalação de programas individuais:
    
    ```bash
    choco feature enable -n allowGlobalConfirmation
    ```
* Use o comando `choco` para instalar as seguintes depêndencias:

    ```bash
    choco install cmake --installargs 'ADD_CMAKE_TO_PATH=System'
    choco install ninja gperf python git dtc-msys2 wget unzip
    ```
4. Feche a janela atual do `cmd.exe` e reabra como administrador para continuar.

## Obtendo o Zephyr-rtos e depêndencias do Python

Para começar, é recomendado a criação de um diretório em seu local de preferência antes da execução dos próximos passos. Neste tutorial utilizaremos um diretório chamado `workspace`.

1. Em seu terminal execute o seguinte comando para instalar o [west](https://docs.zephyrproject.org/latest/develop/west/index.html):

    ```bash
    pip3 install -U west
    ```
2. Obtenha o código fonte do Zephyr:

    ```bash
    cd workspace
    west init zephyrproject
    ````

* Neste ponto, a seguinte estrutura de diretórios deve está montada: 

    ```
    workspace/
    └──zephyrproject/
    ```

3. Em seguida, vá para o diretório `zephyrproject` e utilize o seguinte comando:

    ```bash
    cd zephyrproject
    west update
    ```

4. Exporte o pacote Zephyr-CMake. Isso permite que o CMake carregue automaticamente o código necessário para criar projetos com o Zephyr:
    
    ```bash
    west zephyr-export
    ```

5. Instales as depêndencias adicionais do Python:

    ```bash
    pip3 install -r workspace\zephyrproject\zephyr\scripts\requirements.txt
    ```

## Instale o Zephyr SDK

Ainda na janela do `cmd.exe`.

1. Vá para o diretório raiz:

    ```bash
    cd workspace
    ```
2. Baixe o pacote [Zephyr SDK](https://github.com/zephyrproject-rtos/sdk-ng/releases) mais recente:

    ```bash
    wget https://github.com/zephyrproject-rtos/sdk-ng/releases/download/v0.15.2/zephyr-sdk-0.15.2_windows-x86_64.zip
    ```

3. Exexute a extração dos dos arquivos:

    ```bash
    unzip zephyr-sdk-0.15.2_windows-x86_64.zip
    ```

4. Ao fim do passo **3** a seguinte estrutura de diretórios deve está montada:

    ```
    workspace/
    ├──zephyrproject/
    └──zephyr-sdk-0.15.2/
    ```

Caso a estrutura não esteja de acordo, garanta que ambas as pastas `zephyrproject` e `zephyr-sdk-0.15.2` estejam no mesmo espaço de trabalho.


