# 🧠 Mental Health Tech Survey
Análise de uma pesquisa sobre saúde mental com funcionários da área Tech.

# 👀 Visão Geral do Projeto: 

Nossa empresa presta serviços de prevenção e promoção a saúde mental. Através da pesquisa realizada desejamos entender o perfil dos profissionais que atuam na área da tecnologia e qual a percepção dos mesmos sobre os cuidados com saúde mental.

# 🕵️ Visão Geral & Preparação dos Dados: 

- Variáveis numéricas: Age, ID, no_employees
- Variáveis categóricas: gender, country, state, self_employed, family_history, treatment, work_interference, remote_work, tech_company, benefits, care_options, wellness_program, seek_help, anonimity, leave, mental_health_consequence, phys_health_consequences, coworkers, supervisor, mental_health_interview, physical_health_interview, mental_vs_physical, obs_consequence, faixa_etaria.

- Variáveis criadas: ID, faixa_etaria, tamanho_da_empresa.

- 🧹Limpeza dos dados:
1. Cabeçalhos promovidos.
2. Na coluna "Gender" Os valores 'M','male', 'm', 'Male-ish', 'maile', 'something kinda male?', 'Cis Male', 'Mal', 'Male (CIS)', 'Make', 'Guy (-ish) ^_^' , 'male leaning androgynous', 'Male ',  'Man', 'msle' ,'Mail' , 'cis male', 'Malr', 'Man',  'ostensibly male'  foram substituídos por Male.
3. Na coluna "Gender" Os valores 'female',  'Cis Female', 'F' ,'Woman' 'f','Femake', 'woman', 'Female ', 'cis-female/femme', 'Female (cis)', 'femail' foram substituídos por Female.
4. Na coluna "Gender" Os valores 'Trans-female', 'queer/she/they', 'non-binary' ,'Nah', 'All', 'Enby', 'fluid', 'Genderqueer','Androgyne', 'Agender','Trans woman','Neuter', 'Female (trans)', 'queer' foram substituídos por LGBTQIAPN+.
5. Colçuna "Timestamp" removida.
6. Na coluna Age os Valores 99999999, -1726, -29, 329, 8, 5 foram substituídos por null.
   6.1 Coluna Age ordenada de forma Descendente.
   6.2 Substituição dos valores null com "Preenchido abaixo".
7. Texto da coluna "Country" aparado e limpo. (Trim e Clean"
8. Criação da Coluna faixa_etaria com o código:
   
   ```m
   #"Personalização Adicionada" = Table.AddColumn(#"Linhas Filtradas1", "Faixa Etária", each if [Age] <= 25 then "18-25" else if [Age] <= 35 then "26-35" else if [Age] <= 45 then "36-45" else if [Age] <= 55 then "46-55" else if [Age] <= 65 then "56-65" else "65+")
   ```
   
10. Criação da coluna id para auxiliar na contagem das linhas.
11. Criação da coluna tamanho da empresa com o código:
     ```dax
     - Tamanho da Empresa = SWITCH(
    TRUE(),
    survey[no_employees] = "1-5", "Micro Empresa",
    survey[no_employees] = "6-25", "Pequena empresa",
    survey[no_employees] = "26-100", "Média Empresa",
    survey[no_employees] = "100-500", "Grande Empresa","Big Tech")

    ```
# 🔬 Análise dos Resultados:

1. Perfil dos Participantes
- Participaram da pesquisa 1259 pessoas.
- Sendo a Média de Idade de 31,88 anos.
- A maioria dos entrevistados estão entre 26-35 anos (701 pessoas)
- Dos participantes 78.63% se identificam com o gênero Masculino.
- 70.14% dos entrevistados trabalham de forma presencial.
- Quando perguntados sobre Histórico Familiar , 767 pessoas relataram possuir Histórico de problemas relacionados a Sáude Mental.
- 27.16% dos participantes trabalham em Empresas Big Tech.

2. Percepção dos participantes com Relação a Saúde Mental;
- 39.79% dos participantes não tem conhecimento das opções oferecidas pela empresa sobre cuidado mental.
- 842 pessoas afirmam que não é discutido saúde mental nos programas de Bem-Estar da empresa.]
- 50.60% das pessoas relataram ter buscado tratamento quando perceberam sintomas relacionados a sáude mental.
- Apenas 477 pessoas afirmam que a empresa fornecede programas de cuidado a Saúde Mental.
- 477 pessoas relatarm ter percebido consequências pessoais quando conversaram com seus supervisores sobre saúde mental.
- E 36.93% dos participantes perceberam impacto no seu trabalho quando começaram a apresentar problemas de saúde mental.


# Evolução & Próximos Passos: 
- Criação de um Modelo de predição baseado nos dados obtidos.

## Link do Dashboard: https://app.powerbi.com/view?r=eyJrIjoiYTUxMjljZGUtYjlhNC00MTZlLTk5ODktYjlhZGQ3OTY4ZDY3IiwidCI6IjQyOTJlZGZlLTcxN2QtNDgxYy1hZmQwLWUwNWU3NzJiNjhiMiJ9

