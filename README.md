# Desafio de Modelagem Dimensional

Vamos criar um Star Schema onde 'Professor' será nosso objeto de análise.

![tabela_fato]()

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
