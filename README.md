# runrunitNameConfig

Este repositório contém os arquivos de configuração (**CSV**) usados pelo **Gerador de Nomes de Projeto**. O objetivo é manter, de forma organizada, as informações de **equipes**, **tipos** e **objetivos** para que o gerador possa popular dinamicamente os campos de seleção.

## Estrutura do Repositório

- **teams.csv**  
  Lista de arquivos CSV de equipes. Cada linha (após o cabeçalho) representa o nome de um arquivo CSV que indica uma equipe específica. Por exemplo, `RAID.csv`, `SW.csv`, `TI.csv`, etc.
  
- **[NOME_EQUIPE].csv**  
  Cada arquivo de equipe (por exemplo, `RAID.csv`) especifica as colunas de **Tipo** e **Objetivo** a serem usadas na geração de nomes.

### 1. O que é `teams.csv`?

O arquivo `teams.csv` é responsável por **listar quais equipes** estão disponíveis.  
Ele deve ter uma linha de cabeçalho (ex.: `TEAM_FILE`) e, em seguida, cada linha representa um arquivo (ex.: `RAID.csv`) que contém os dados daquela equipe.

**Exemplo de `teams.csv`:**

```csv
TEAM_FILE
RAID.csv
SW.csv
FLEX.csv
SMD.csv
TI.csv
```

Neste exemplo, temos 5 equipes: RAID, SW, FLEX, SMD e TI. Cada uma delas terá seu próprio arquivo CSV correspondente.

### 2. O que são os arquivos de equipe (ex.: RAID.csv)?

Cada arquivo de equipe descreve as possíveis combinações de Tipo e Objetivo que o gerador deve exibir. O formato deve ser:

- Uma linha de cabeçalho contendo `TIPO,OBJETIVO`.
- Seguido por diversas linhas, cada uma com 2 colunas:
  - A primeira coluna é o Tipo (ex.: `HW`, `FW`, `MC` etc.).
  - A segunda coluna é o Objetivo (ex.: DESENV, MELHORIA, OTIM etc.).

**Exemplo de `EQUIPX.csv`:**

```csv
TIPO,OBJETIVO
HW,DESENV
FW,UPGRADE
HW,OTIM
MC,AUX
```

Isso indica que, para a equipe `EQUIPX`, existem 4 possíveis combinações de Tipo e Objetivo:

- Tipo = HW e Objetivo = DESENV
- Tipo = FW e Objetivo = UPGRADE
- Tipo = HW e Objetivo = OTIM
- Tipo = MC e Objetivo = AUX
  
O gerador de nomes vai ler esse arquivo e preencher os seletores de ?Tipo? e ?Objetivo? com estes valores.

### 3. Como criar ou editar Equipes, Tipos e Objetivos

**1 - Adicionar uma nova Equipe**

- Abra o arquivo teams.csv.
- Adicione uma nova linha com o nome do arquivo CSV, por exemplo, MEP.csv.
- Crie um novo arquivo MEP.csv no mesmo repositório, com a estrutura:

```csv
TIPO,OBJETIVO
[tipo1],[objetivo1]
[tipo2],[objetivo2]
```

- Faça commit dessas alterações.
  
**2 - Remover ou renomear uma Equipe**

- Se quiser remover, basta apagar a linha correspondente em teams.csv e deletar o arquivo CSV da equipe.
- Para renomear, altere o nome tanto em teams.csv quanto no próprio arquivo CSV.
  
**3 - Editar Tipos/Objetivos de uma Equipe**

- Localize o arquivo da equipe, por exemplo, RAID.csv.
- Abra o arquivo e modifique as linhas (adicionando, removendo ou renomeando colunas TIPO e OBJETIVO).
- Salve e faça commit.

### 4. Regras de Formatação

- Arquivo `teams.csv`
  - Deve ter um cabeçalho (`TEAM_FILE`).
  - Cada linha subsequente é o nome de um arquivo CSV (ex.: `RAID.csv`).
- Arquivos de Equipe
  - Devem conter duas colunas: TIPO e OBJETIVO.
  - A primeira linha (cabeçalho) deve ser TIPO,OBJETIVO.
  - Cada linha seguinte deve ser uma combinação de TIPO e OBJETIVO.
  - Não é necessário ter a mesma quantidade de tipos e objetivos.
