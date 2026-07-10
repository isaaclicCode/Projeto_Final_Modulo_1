# Projeto_Final_Modulo_1_Aluno_Isaac_Trenard

# 🏢 Projeto RH - Análise de Salários e Distribuição Geográfica

**Aluno:** Isaac Trenard  
**Turma:** Visualização de Dados e Business Intelligence [T2]  
**Módulo:** 1 - Semana 13  

---

## 🎯 Objetivo do Projeto

Este projeto tem como objetivo aplicar e consolidar todos os conhecimentos adquiridos ao longo do curso **SC Tech — Visualização de Dados e Business Intelligence [T2]**, integrando as principais ferramentas utilizadas no dia a dia de um analista de dados: VS Code, Banco de Dados FreeSQL e linguagem Python.

A partir de uma base de dados de Recursos Humanos (RH), a análise busca responder a perguntas estratégicas sobre a estrutura salarial da empresa, explorando:

- A distribuição dos salários por departamento e cargo;
- A distribuição geográfica dos funcionários (cidade, estado ou país);
- Padrões de remuneração e a identificação de possíveis outliers.

O projeto simula uma demanda real da área de RH, onde o objetivo é transformar dados brutos em informações claras e úteis para a tomada de decisão, colocando em prática os conceitos e ferramentas desenvolvidos durante o curso.

---

## 📊 Tabelas Utilizadas

As seguintes tabelas do esquema **HR** do banco FreeSQL foram utilizadas:

| Tabela | Descrição |
|--------|-----------|
| `EMPLOYEES` | Dados dos funcionários (salário, cargo, departamento) |
| `DEPARTMENTS` | Informações sobre os departamentos |
| `JOBS` | Detalhes dos cargos (título, faixa salarial) |
| `LOCATIONS` | Localização dos departamentos |
| `COUNTRIES` | Nomes dos países |
| `REGIONS` | Nomes das regiões |

## 📝 Consultas SQL

### Query 1 - Salário por Departamento e Cargo
**Objetivo:** Analisar a distribuição de salários por departamento e cargo.

```sql
-- Query 1
SELECT
    e.EMPLOYEE_ID,
    e.FIRST_NAME,
    e.LAST_NAME,
    e.SALARY,
    d.DEPARTMENT_NAME,
    d.DEPARTMENT_ID,
    j.JOB_TITLE,
    j.JOB_ID
FROM HR.EMPLOYEES e
LEFT JOIN HR.DEPARTMENTS d ON e.DEPARTMENT_ID = d.DEPARTMENT_ID
LEFT JOIN HR.JOBS j ON e.JOB_ID = j.JOB_ID
WHERE e.SALARY IS NOT NULL
ORDER BY e.SALARY DESC

### Query 2 - Funcionários por Região (com localização)
Objetivo: Analisar salários e distribuição geográfica dos funcionários.

sql
-- Query 2
SELECT
    e.EMPLOYEE_ID,
    e.FIRST_NAME,
    e.LAST_NAME,
    e.SALARY,
    d.DEPARTMENT_NAME,
    l.CITY,
    c.COUNTRY_NAME,
    r.REGION_NAME
FROM HR.EMPLOYEES e
LEFT JOIN HR.DEPARTMENTS d ON e.DEPARTMENT_ID = d.DEPARTMENT_ID
LEFT JOIN HR.LOCATIONS l ON d.LOCATION_ID = l.LOCATION_ID
LEFT JOIN HR.COUNTRIES c ON l.COUNTRY_ID = c.COUNTRY_ID
LEFT JOIN HR.REGIONS r ON c.REGION_ID = r.REGION_ID
WHERE e.SALARY IS NOT NULL
ORDER BY e.SALARY DESC;


# EM CONSTRUÇÃO
