
# Teste de criação de um modelo de automação usando Machine Learning no Microsoft Azure.





## Passo 1: Criação de um Recurso de Machine Learning

1. Inicialmente é necessário fazer a criação de um recurso. Para isso,  pressione "Criar recurso" e na sequência selecione "Azure Machine Learning".

2. Na tela de edição de recurso, informe qual é a sua subscrição, grupo de recursos (crie um se ainda não tiver), dê um nome para sua área de trabalho, selecione a região (dica: East US, mais barato) e a conta de armazenamento.

3. Em seguida, pressione Criar e a sua área de trabalho do recurso será criada.

4. Aperte "Ir para recurso" e após isso em "Iniciar o estúdio".


## Passo 2: Criação do trabalho de ML automatizado


1. No menu lateral do estúdio, encontre ML automatizado e clique em "Novo trabalho de ML automatizado".

2. Nas "Configurações básicas", preencha os campos "Nome do trabalho", "Novo nome do experimento" e "Descrição".

3. Na seção "Tipo de tarefa e dados", selecione o tipo de tarefa como Regressão.

4. Em "Selecionar dados", clique em "Criar", vai abrir um modal. 

5. No modal que acabou de abrir, em "Tipos de dados", preencha os campos "Nome", "Descrição" e o "Tipo" pode ser selecionado o Tabular. 

6. Pressione "Avançar". 

7. No passo "Fonte de dados", escolha "De arquivos da Web" e avance.

8. Na sequência, em "URL da Web", informe a URL https://aka.ms/bike-rentals.

9. Em "Configurações", preencha as configurações do conjunto e após avançar para "Esquema".

10. Avance mais uma vez e verifique as configurações criadas para o ativo de dados e pressione criar.

11. Em "Configurações de tarefas", escolha o conjunto de dados importado. 

12. Em "Coluna de destino" escolha a coluna rentals como target.

13. Nos campos de "Limite", preencha com os valores a seguir:

- Máximo de avaliações: 3
- Máximo de avaliações simultâneas: 3
- Máximo de nós: 3
- Limite de pontuação da métrica: 0,085
- Tempo limite do experimento (minutos): 15
- Tempo limite de iteração (minutos): 15

14. Pressione "Habilitar encerramento antecipado".

15. Na seção "Validar e testar", no campo de  "Tipo de validação" escolha "Divisão de validação de treinamento".

16. Na seção de "Computação", use a seguite configuração:
- Selecione o tipo de computação: Sem servidor
- Tipo de máquina virtual: CPU 
- Tipo de máquina virtual: Dedicado
- Tamanho da máquina virtual: A padrão que aparecer
- Número de Instâncias: 1

17. Pressione avançar.

18. Por fim, pressione "Enviar trabalho de treinamento".

## Passo 3: Crie um Modelo


1. Acesse a página do trabalho realizado e pressione "Modelo de registro".

2. Deixe as opções padrões para "Selecionar saída". 

3. Em "Configurações do modelo", preencha o nome e a versão. 

4. Clique em criar o modelo.
## Passo 4: Teste do Modelo

1. No menu, acesse "Pontos de extremidade".

2. Clique em "Criar" e em seguida marque o modelo.

3. Deixe todos os campos com os valores padrões, exceto "Contagem de instâncias", deixe esse como 1.

4. Por fim, pressione "Implantar".

5. Em seguida, vai ser processado e vai demorar um pouco.

6. No ponto de extremidade, quando tiver tudo pronto informe os dados do JSON abaixo e pressione "Testar":

<code>
{
  "input_data": {
    "data": [
       {
         "day": 1,
         "mnth": 1,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]
  }
}
</code>

7. O resultado obtido foi esse: 
<code>
[1 item
    0:float341.203802832822
]
</code>
