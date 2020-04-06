## 2. Exercícios de Funções Agregadas

1. Quais são os valores máximo e mínimo das seguintes colunas:
    * total
    * hp
    * ataque
    * defesa
    * ataque_especial
    * defesa_especial
    * velocidade
    * taxa_captura

```sql
select max(total), min(total), 
max(hp), min(hp), 
max(ataque), min(ataque),
max(defesa), min(defesa),
max(ataque_especial), min(ataque_especial),
max(defesa_especial), min(defesa_especial),
max(velocidade), min(velocidade),
max(ataque), min(ataque),
max(taxa_captura), min(taxa_captura)
from pokemon;
```

2. Quantas cores diferentes possuem os pokémons?

```sql
select count(distinct cor)
from pokemon;
```

3. Qual é o peso médio dos pokémons?

```sql
select avg(peso_kg)
from pokemon;
```

4. Qual é a soma das alturas dos pokémons?

```sql
select sum(altura_m)
from pokemon;
```

5. Quantos pokémons estão cadastrados no banco de dados?

```sql
select count(nome)
from pokemon;
```

6. Qual é o altura média dos pokémons?

```sql
select avg(altura_m)
from pokemon;
```

7. Qual é o desvio padrão do valor de HP dos pokémons?
```sql
select STD(hp)
from pokemon;
```

8. Quantos pokémons possuem tipo2?

```sql
select count(tipo2)
from pokemon
where tipo2 is not null;
```

9. Quantos são os diferentes tipos primários dos pokémons? 

```sql
select count(distinct nome)
from pokemon
where geracao = 1;
```

10. Qual é a soma dos pesos dos pokémons?

```sql
select sum(peso_kg)
from pokemon;
```

11. Qual é a quantidade de Pokémons lendários e não lendários

```sql
select lendario, count(lendario) as qdt
from pokemon 
group by lendario;
```

12. Qual é a quantidade de pokémons para cada uma das diferentes cores ordenadas decrescente?

```sql
select cor, count(cor) as qdt
from pokemon 
group by cor
order by cor desc;
```

13. Qual é a média de peso e altura de cada um dos tipos primários dos pokémons? Ordene os resultados decrescente respectivamente por média de peso e altura.
```sql
select nome, avg(peso_kg) as media_peso, avg(altura_m) as media_altura
from pokemon 
group by tipo1
order by media_peso, media_altura;
```

14. Qual é a taxa de captura média por cor de cada um dos pokémons lendários?
```sql
select cor, count(cor) as cor
from pokemon
where lendario = 1
group by cor;
```

15. Qual os tipos primários que possuem a taxa de captura média acima de 100?
```sql
select nome, taxa_captura
from pokemon
where geracao = 1 and taxa_captura > 100;
```

16. Agrupados por cor, quais pokémons não lendários possuem média total abaixo de 400
```sql
select cor, avg(taxa_captura) as taxa_captura
from pokemon
where taxa_captura < 400 and lendario=0
group by cor;
```

17. Qual o valor máximo total em cada uma das gerações?	
```sql
select geracao, count(nome) as qdt_pokemon
from pokemon
group by geracao;
```

18. Quantos pokémons lendários existem em cada uma das gerações?
```sql
select geracao, count(nome) as pokemon_lendario
from pokemon
where lendario = 1
group by geracao;
```

19. Em cada uma das gerações, quantos pokémons tem tipos primários e secundários e qual a taxa_captura média deles?
```sql
select geracao, count(nome), avg(taxa_captura)
from pokemon
where tipo1 is not null and tipo2 is not null
group by geracao;
```

20. Qual é a quantidade de cores de cada um dos pokémons lendários em todas as gerações?
```sql
select geracao, count(cor)
from pokemon
where lendario = 1
group by geracao;
```


## REFERÊNCIAS

* [Webiste Oficial - Pokémon](https://www.pokemon.com/br/guia-para-pais/)
* [Guia de Estilo SQL · SQL Style Guide](https://www.sqlstyle.guide/pt-br/)







