# Processo de Modelagem Dimensional – Star Schema para Análise de Professores

Este repositório contém a solução do desafio de construção de um **Star Schema (Esquema em Estrela)** com foco no objeto de análise **Professor**[cite: 5], desenvolvido para o bootcamp da DIO.

## 📌 Objetivo do Desafio
Transformar um diagrama relacional de uma universidade em um modelo dimensional otimizado[cite: 5]. O foco principal da análise são os **Professores**, seus cursos ministrados, departamentos e datas de oferta de disciplinas[cite: 5]. Conforme instruído, os dados referentes a alunos foram desconsiderados na modelagem[cite: 5].

---

## 📐 Estrutura do Modelo Dimensional (Star Schema)

### **1. Tabela Fato (`Fato_Professor`)**
Contém as métricas de ensino, carga horária e os eventos de lecionação do professor[cite: 5]:
* `SK_Fato_Professor` (Surrogate Key)
* `idProfessor` (FK - Dim_Professor)
* `idDepartamento` (FK - Dim_Departamento)
* `idDisciplina` (FK - Dim_Disciplina)
* `idCurso` (FK - Dim_Curso)
* `idData_Oferta` (FK - Dim_Data)
* `Carga_Horaria_Ministrada` (Métrica)
* `Qtd_Disciplinas_Lecionadas` (Métrica)
* `Qtd_Cursos_Atendidos` (Métrica)

---

### **2. Tabelas Dimensão**

* **`Dim_Professor`**
  * `idProfessor` (PK)
  * `Nome_Professor`
  * `Campus`
  * `Coordenador` (Sim/Não)

* **`Dim_Departamento`**
  * `idDepartamento` (PK)
  * `Nome_Departamento`
  * `Campus`
  * `idProfessor_Coordenador`

* **`Dim_Disciplina`**
  * `idDisciplina` (PK)
  * `Nome_Disciplina`
  * `Carga_Horaria`
  * `Possui_Pre_Requisito` (Sim/Não)

* **`Dim_Curso`**
  * `idCurso` (PK)
  * `Nome_Curso`
  * `Tipo_Graduacao`

* **`Dim_Data` (Dimensão de Datas Criada)**[cite: 5]
  * `idData` (PK)
  * `Data_Oferta`
  * `Ano`
  * `Semestre`
  * `Trimestre`
  * `Mes`
  * `Nome_Mes`

---

## 🛠️ Etapas do Projeto
1. **Análise do Diagrama Relacional:** Identificação das entidades relacionadas ao Professor (Departamento, Disciplina, Curso)[cite: 5].
2. **Exclusão do Escopo de Alunos:** Remoção das tabelas `Aluno` e `Matriculado`[cite: 5].
3. **Criação da Dimensão Data:** Adição de campos temporais de oferta de disciplinas e cursos para habilitar Time Intelligence no Power BI[cite: 5].
4. **Definição de Granularidade e Chaves:** Mapeamento de Primary Keys (PK), Foreign Keys (FK) e criação da Surrogate Key na tabela Fato[cite: 5].
5. **Configuração de Relacionamentos:** Estabelecimento de conexões `1:N` da Fato para as Dimensões (Star Schema)[cite: 5].

---

## 📂 Arquivos no Repositório
* `Modelagem_StarSchema_Universidade.pbix`: Modelo dimensional no Power BI Desktop.
* `Diagrama_Star_Schema.png`: Imagem do diagrama em estrela resultante.
* `README.md`: Documentação completa.
