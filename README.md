# 😷️🇵🇹 Dados relativos à pandemia COVID-19 em Portugal 

📅️ **Última actualização**: 14 de Março de 2020, 15h
ℹ️ **Fonte dos dados**: [Direcção Geral de Saúde](https://www.dgs.pt/), Ministério da Saúde Português, através do _dashboard_ do COVID-19 ([aqui](https://covid19.min-saude.pt/ponto-de-situacao-atual-em-portugal/)  e dos [relatórios de situação publicados diariamente](https://covid19.min-saude.pt/relatorio-de-situacao/) desde 03/03/2020.

# 🤔 Contexto

Embora a comunicação e partilha de dados por parte do Ministério de Saúde Português tenha melhorado consideravelmente ao longo da crise do COVID-19, ainda está longe de ideal (havendo a destacar o exemplo do [repositório da Protecção Civil Italiana no GitHub](https://github.com/pcm-dpc/COVID-19).

A informação disponibilizada pela Direcção Geral de Saúde (DGS), para além de não ter o nível de granularidade da das autoridades italianas, também não é disponibilizada em formatos abertos e facilmente inspeccionáveis/ manipuláveis. Ficam assim dificultadas tarefas de análise, modelação e visualização por parte da comunidade (quer mais informal, quer mais académica/industrial) disposta a colaborar no combate à pandemia com as ferramentas do seu dia-a-dia: as de análise de dados.

❗ O compromisso deste repositório é justamente esse: **todos os dias enquanto esta pandemia durar, o ficheiro `data.csv` será actualizado com a informação mais recente disponibilizada pela Direcção Geral de Saúde nesse dia**. Esta informação será extraída do relatório de situação o mais rapidamente possível após a sua disponibilização (que costuma ser ~12h00 GMT+00:00). 

A estrutura base deste ficheiro, desenhada para fácil manipulação em Excel/Python/R não mudará, podendo a comunidade analítica considerá-lo um alvo imutável (em termos de localização e estrutura). Este poderá, por exemplo, ser usado para alimentar plataformas _online_ de visualização/modelação. De notar que, mediante a evolução do formato dos relatórios de situação, ser adicionadas novas colunas.

_Porque tudo começa com bons dados._

# 🧱 Estrutura

O repositório está organizado da seguinte forma:
+ `data.csv`: o Pastel de Nata. 
+ `archive/`: arquivo de todos os relatórios de situação disponibilizados pela DGS, em formato `.pdf`. Os relatórios são disponibilizados diariamente, desde o dia 03-03-2020.
+ `notebooks/`: contém um pequeno _notebook_ Python com um pequeno exemplo de como abrir, interagir e navegar pelos dados. **A análise exemplo aí efectuada tem zero valor científico/clínico**.

# 📔 Dicionário dos dados

Uma explicação do conteúdo em `data.csv`. 

📝 _ARS_: Administração Regional de Saúde 

| Nome da coluna        | Significado           | Possíveis valores  |
| ------------- |:-------------:| -----:|
| data      | Data de publicação dos dados (nem sempre os dados reflectem a realidade desse dia, podendo nalguns casos ser relativos a algumas horas antes) | Uma data no formato DD-MM-YYYY |
| confirmados      | Casos confirmados      |   Um inteiro >= 0 |
| confirmados_arsnorte | Casos confirmados na ARS Norte      |    Um inteiro >= 0 |
| confirmados_arscentro | Casos confirmados na ARS Centro      |    Um inteiro >= 0 |
| confirmados_arslvt | Casos confirmados na ARS Lisboa e Vale do Tejo      |    Um inteiro >= 0 |
| confirmados_alentejo | Casos confirmados na ARS Alentejo     |    Um inteiro >= 0 |
| confirmados_arsalgarve | Casos confirmados na ARS Algarve    |    Um inteiro >= 0 |
| confirmados_acores | Casos confirmados na Região Autónoma dos Açores |    Um inteiro >= 0 |
| confirmados_madeira | Casos confirmados na Região Autónoma da Madeira  |    Um inteiro >= 0 |
| confirmados_estrangeiro | Casos confirmados no estrangeiro    |    Um inteiro >= 0 ou `NaN` para os dias em que a DGS não reportava este indicador  |
| confirmados_novos | Total de novos casos confirmados comparativamente ao dia anterior |  Um inteiro >= 0 |
| recuperados | Total de casos recuperados | Um inteiro >= 0 |
| obitos | Total de óbitos |  Um inteiro >= 0 |
| internados | Total de pacientes COVID-19 internados |   Um inteiro >= 0 ou `NaN` para os dias em que a DGS não reportava este indicador |
| internados_uci | Número de pacientes COVID-19 internados em Unidades de Cuidado Intensivos |  Um inteiro >= 0 ou `NaN` para os dias em que a DGS não reportava este indicador |
| lab | Total de casos suspeitos a aguardar resultados laboratoriais    |  Um inteiro >= 0 ou `NaN` para os dias em que a DGS não reportava este indicador |
| suspeitos |   Total de casos suspeitos ([tendo a definição sido actualizada a 29/03/2020[(https://www.dgs.pt/directrizes-da-dgs/orientacoes-e-circulares-informativas/orientacao-n-002a2020-de-25012020-atualizada-a-250220201.aspx))   |     Um inteiro >= 0 |
| vigilancia | Total de casos sob vigilância pelas autoridades de saúde     |    Um inteiro >= 0 ou `NaN` para os dias em que a DGS não reportava este indicador |
| cadeias_transmissao | Número de cadeias de transmissão do SARS-CoV-2 activas  |   Um inteiro >= 0 ou `NaN` para os dias em que a DGS não reportava este indicador |
| transmissao_importada | Número de casos confirmados com transmissão por via de infectados de outros países      |   Um inteiro >= 0 ou `NaN` para os dias em que a DGS não reportava este indicador |
| transmissao_comunitaria | Número de casos confirmados com transmissão através da respectiva comunidade local   |   Um inteiro >= 0 ou `NaN` para os dias em que a DGS não reportava este indicador |

Relativamente à coluna `data`, esta corresponde à data em que a DGS disponibilizou esta informação, que nem sempre corresponde à data em que foi recolhida. A partir de 03-03-2020, é possível verificar no respectivo relatório de situação (disponível na pasta `archive`) qual a data de recolha da informação apresentada. 

Nos seus relatórios de situação, a DGS reporta alguma informação epidemiológica extra, como género e grupo etário dos infectados, que poderão ser adicionados mais tarde. 

Uma outra métrica adicional e com potencial interesse científico, o número de casos com base na data de início de sintomas, é também reportada pela DGS. No entanto, é apenas disponibilizada um gráfico de eixos esparsos, o que pode introduzir erros de aproximação e comprometer a factualidade dos dados. Por essa razão, esta informação é propositadamente excluída. 

# 💡 Problemas, inconsistências e melhorias

Quaisquer sugestões de dados complementares (provindos de fontes oficiais), inconsistências nos dados ou melhorias, à vontade ➡️ _Issues_ ou _Pull Requests_.