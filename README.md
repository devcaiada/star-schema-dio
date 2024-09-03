# Desafio de Modelagem Dimensional

Vamos criar um Star Schema onde 'Professor' será nossa tabela fato para objeto de análise.

![tabela_fato](https://github.com/devcaiada/star-schema-professor/blob/main/assets/Fato_Professor.png?raw=true)

## Tabela Fato: Fato_Professor

- ID_Professor (chave primária)
- ID_Curso (chave estrangeira)
- ID_Departamento (chave estrangeira)
- ID_Data (chave estrangeira)
- Horas_Ensino (medida)
- Salario (medida)
- Publicacoes (medida)
- Avaliacoes (medida)

## Tabelas Dimensão

### Dim_Professor

- ID_Professor (chave primária)
- Nome_Professor
- Titulo_Academico
- Especialidade
- Anos_Experiencia

### Dim_Curso

- ID_Curso (chave primária)
- Nome_Curso
- Nivel_Curso (graduação, pós-graduação, mba, mestrado, doutorado)
- Carga_Horaria

### Dim_Departamento

- ID_Departamento (chave primária)
- Nome_Departamento
- Chefe_Departamento

### Dim_Data

- ID_Data (chave primária)
- Data
- Ano
- Mes
- Dia
- Trimestre
- Semestre

## Relacionamentos

- **Fato_Professor** se relaciona com **Dim_Professor** através de **ID_Professor**.
- **Fato_Professor** se relaciona com **Dim_Curso** através de **ID_Curso**.
- **Fato_Professor** se relaciona com **Dim_Departamento** através de **ID_Departamento**.
- **Fato_Professor** se relaciona com **Dim_Data** através de **ID_Data**.

## Granularidade

A tabela data foi ajustada para diferentes níveis de granularidade como Ano, Mês, Dia, Trimestre e Semestre.

---

<br>
<br>
</br>

# Star Schema Financials com DAX

![Star_schema](https://github.com/devcaiada/star-schema-professor/blob/main/assets/Star_schema_financial.png?raw=true)

Utilizaremos a tabela única de Financial Sample para criar as tabelas dimensão e fato do nosso modelo baseado em star schema.

O processo consiste na criação das tabelas com base na tabela original. A partir da cópia serão selecionadas as colunas que irão compor a visão da nova tabela.

![dados](https://github.com/devcaiada/star-schema-professor/blob/main/assets/Dados.png?raw=true)

Ciramos a tabela Fato Vendas (**F_Vendas**) e a partir da tabela **financials** criamos as tabelas dimensão:

- **D_Produtos** (ID_produto, Produto, Média de Unidades Vendidas, Médias do valor de vendas, Mediana do valor de vendas, Valor máximo de Venda, Valor mínimo de Venda)

- **D_Descontos** (ID_produto, Discount, Discount Band)

- **D_Produtos_Detalhes** (ID_produtos, Discount Band, Sale Price, Units Sold, Manufactoring Price)

- **D_Detalhes** (\*)

- **D_Data** – Criada por DAX com calendar()

- **F_Vendas** (SK_ID , ID_Produto, Produto, Units Sold, Sales Price, Discount Band, Segment, Country, Salers, Profit, Date (campos))

## Tabela Data com DAX

![date](https://github.com/devcaiada/star-schema-professor/blob/main/assets/Date.png?raw=true)

Para a criação da tabela **D_Data** utilizamos **DAX** com as respectivas funções:

- **CALENDARAUTO** - Para a criação da tabela.
- **YEAR** - Para adicionar a coluna Ano (Year).
- **MONTH** - Para a coluna Mês (Month Number).
- **WEEKNUM** - Para a semana (Week Number).
- **WEEKDAY** - Para adicionarmos o dia da semana (Day of the week).
- **FORMAT** - Com o parâmetro "DDDD" para a coluna dia da semana (Weeks Day).
