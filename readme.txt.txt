Projeto realizado por Thiago Limeira Mendes Roland

Projeto simples com o intuito de treinar DDL de SQL (através da criação de novas tabelas com constraints e relações entre si), geração de dados artificiais com Python e biblioteca Faker e modelagem (através de esquema estrela), normalização e análise dos dados com o Power BI.

Ferramentas utilizadas:
- SQLite
- PowerBI

Linguagens utilizadas
- SQL
- Python
- DAX no Power BI

O projeto consistiu na criação de um banco de dados inicial (intitulado escopo.db na pasta) com 6 tabelas no total, sendo uma a tabela-fato (fato_vendas) e as 5 restantes tabelas-dimensão. Foram criadas primeiro as tabelas-dimensão, para assim serem criadas as primary keys destas tabelas que iriam referenciar a tabela-fato, e por último a tabela-fato, a maioria destas tabelas com constraints visando a padronização dos dados para assim facilitar a limpeza e exploração.

Em seguida, foi escrito um script em Python para gerar dados aleatórios (dados sintéticos) para a realização do projeto. Foram escolhidos dados sintéticos devido ao desejo tanto de integrar Python com SQL e Power BI quanto também pela intenção de que os dados, por natureza, viessem com bastante problemas e necessitando de normalização (visto que dados sintéticos dificilmente se enquadram completamente na regra de negócio).

Após a criação de uma nova database (projetoecommerce.db) baseada na escopo.db, comecei o trabalho com o PowerBI. De início, houve vários problemas: Nem todas as tabelas estavam com o diagrama entidade-relacionamento estabelecido, a tabela dim_calendario não estava automaticamente ligando-se à tabela central fato vendas. Para resolver isto, tive de alterar o tipo de chave referenciada para data (inglês), visto que os dados gerados seguem o padrão e formato estado-unidense. Após esta mudança no tipo de dado da linha id_data, as tabelas conseguiram ligar-se e foi firmado o relacionamento.

Também houve problemas quanto aos tipos de dados, duplicidade e conteúdo das linhas: Em várias colunas os tipos de dados estavam incorretos (como colunas de texto quando o tipo do dado era numérico) e o conteúdo das linhas veio padronizado errado, como na coluna subcategoria da tabela dim_produtos, em que todos as linhas começavam por "Subcat x categoria". Foram aplicadas todas as correções possíveis para a database, incluindo a exclusão da coluna Subcategoria, que acabou se tornando apenas uma duplicada de Categoria.

Após toda a limpeza dos dados efetuada, foi feita a análise dos dados: Não foi realizada a análise dos dados à fundo, visto que os dados são sintéticos, de baixa granularidade e baixa sazonalidade, assim não espelhando os dados da vida real. Ainda assim, foram feitos cálculos DAX para chegar-se à algumas métricas desejadas, como calcular a correlação entre o valor dos descontos e o número de vendas dos produtos. Várias conclusões (como baixa correlação entre desconto e aumento de vendas) puderam ser tiradas da análise e exploração dos dados.

Ao término, foram aplicadas medidas de "estilização" e design ao projeto para facilitar a visualização e tornar a leitura e interpretação mais naturais. No total, foram criados 6 arquivos: .gitignore (contendo intruções para Git), escopo (a database inicial na qual treinei DDL), modelagempowerbi (aonde foram feitas a modelagem, limpeza e análise dos dados), projetoecommerce (a database gerada pelo script), readme e script (o script Python para geração dos dados fictícios).

Obrigado pela atenção.