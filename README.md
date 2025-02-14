# runrunitNameConfig

Este reposit�rio cont�m os arquivos de configura��o (**CSV**) usados pelo **Gerador de Nomes de Projeto**. O objetivo � manter, de forma organizada, as informa��es de **equipes**, **tipos** e **objetivos** para que o gerador possa popular dinamicamente os campos de sele��o.

## Estrutura do Reposit�rio

- **teams.csv**  
  Lista de arquivos CSV de equipes. Cada linha (ap�s o cabe�alho) representa o nome de um arquivo CSV que indica uma equipe espec�fica. Por exemplo, `RAID.csv`, `SW.csv`, `TI.csv`, etc.
  
- **[NOME_EQUIPE].csv**  
  Cada arquivo de equipe (por exemplo, `RAID.csv`) especifica as colunas de **Tipo** e **Objetivo** a serem usadas na gera��o de nomes.

### 1. O que � `teams.csv`?

O arquivo `teams.csv` � respons�vel por **listar quais equipes** est�o dispon�veis.  
Ele deve ter uma linha de cabe�alho (ex.: `TEAM_FILE`) e, em seguida, cada linha representa um arquivo (ex.: `RAID.csv`) que cont�m os dados daquela equipe.

**Exemplo de `teams.csv`:**

```csv
TEAM_FILE
RAID.csv
SW.csv
FLEX.csv
SMD.csv
TI.csv
```

Neste exemplo, temos 5 equipes: RAID, SW, FLEX, SMD e TI. Cada uma delas ter� seu pr�prio arquivo CSV correspondente.

### 2. O que s�o os arquivos de equipe (ex.: RAID.csv)?

Cada arquivo de equipe descreve as poss�veis combina��es de Tipo e Objetivo que o gerador deve exibir. O formato deve ser:

- Uma linha de cabe�alho contendo `TIPO,OBJETIVO`.
- Seguido por diversas linhas, cada uma com 2 colunas:
  - A primeira coluna � o Tipo (ex.: `HW`, `FW`, `MC` etc.).
  - A segunda coluna � o Objetivo (ex.: DESENV, MELHORIA, OTIM etc.).

**Exemplo de `EQUIPX.csv`:**

```csv
TIPO,OBJETIVO
HW,DESENV
FW,UPGRADE
HW,OTIM
MC,AUX
```

Isso indica que, para a equipe `EQUIPX`, existem 4 poss�veis combina��es de Tipo e Objetivo:

- Tipo = HW e Objetivo = DESENV
- Tipo = FW e Objetivo = UPGRADE
- Tipo = HW e Objetivo = OTIM
- Tipo = MC e Objetivo = AUX
  
O gerador de nomes vai ler esse arquivo e preencher os seletores de ?Tipo? e ?Objetivo? com estes valores.

### 3. Como criar ou editar Equipes, Tipos e Objetivos

**1 - Adicionar uma nova Equipe**

- Abra o arquivo teams.csv.
- Adicione uma nova linha com o nome do arquivo CSV, por exemplo, MEP.csv.
- Crie um novo arquivo MEP.csv no mesmo reposit�rio, com a estrutura:

```csv
TIPO,OBJETIVO
[tipo1],[objetivo1]
[tipo2],[objetivo2]
```

- Fa�a commit dessas altera��es.
  
**2 - Remover ou renomear uma Equipe**

- Se quiser remover, basta apagar a linha correspondente em teams.csv e deletar o arquivo CSV da equipe.
- Para renomear, altere o nome tanto em teams.csv quanto no pr�prio arquivo CSV.
  
**3 - Editar Tipos/Objetivos de uma Equipe**

- Localize o arquivo da equipe, por exemplo, RAID.csv.
- Abra o arquivo e modifique as linhas (adicionando, removendo ou renomeando colunas TIPO e OBJETIVO).
- Salve e fa�a commit.

### 4. Regras de Formata��o

- Arquivo `teams.csv`
  - Deve ter um cabe�alho (`TEAM_FILE`).
  - Cada linha subsequente � o nome de um arquivo CSV (ex.: `RAID.csv`).
- Arquivos de Equipe
  - Devem conter duas colunas: TIPO e OBJETIVO.
  - A primeira linha (cabe�alho) deve ser TIPO,OBJETIVO.
  - Cada linha seguinte deve ser uma combina��o de TIPO e OBJETIVO.
  - N�o � necess�rio ter a mesma quantidade de tipos e objetivos.
