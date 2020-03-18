## Consultas

1. Selecione o banco de dados (esquema) `pokédex`.

```sql
use pokedex;
```

2. Obtenha informações da estrutura da tabela `Pokémon`.

```sql
desc pokemon;
```

3. Selecione todos os pokémons cadastrados no banco de dados.

```sql
select * from pokemon;
```

4. Selecione o `numero`, `nome`, `cor`, `altura_m` e `peso_kg` de todos os pokémons cadastrados.

```sql
select numero, nome, cor, altura_m, peso_kg from pokemon;
```

5. Qual é o `numero` e o `nome` de todos os pokémons da primeira geração?

```sql
select numero, nome from pokemon where geracao = 1;
```

6. Quais são os pokémons `Amarelo` da primeira geração?

```sql
select * from pokemon where cor = 'Amarelo';
```

7. Qual é o pokémon mais forte?

```sql
select max(ataque) as ataque from pokemon;
```

8. Selecione o `numero`, `nome` e `tipo1`; de todos os pokémons cujo tipo primário é `Fire`.

```sql
select numero, nome, tipo1 from pokemon where tipo1 = 'fire';
```

10. Selecione em ordem decrescente o `numero`, `nome` e `defesa` de todos os pokémons.

```sql
select numero, nome, defesa from pokemon order by numero desc;
```

11. Qual o pokémon possui *menor* taxa de captura? Selecione apenas `numero` e `nome`.

```sql
select numero, nome from pokemon where taxa_captura = (select min(taxa_captura) from pokemon);
```


12. Selecione todos pokémons que não possuem tipo secundário, ou seja, `tipo2`.

```sql
select * from pokemon where tipo2 is null;
```

13. Selecione `numero`, `nome`, `tipo1`, `tipo2` de todos os pokémons que possuem o peso entre 100kg e 500kg.

```sql
select numero, nome , tipo1, tipo2, peso_kg from pokemon where peso_kg between 100 and 500;
```


14. Crie um ranking dos top 10 pokémons mais velozes, contendo `numero`, `nome` e `velocidade`.

```sql
select numero, nome, velocidade from pokemon order by velocidade desc limit 10 ;
``` 


15. Selecione `numero`, `nome`, `tipo1`, `tipo2`, `taxa_captura` dos pokémons que possuem os dois tipos e tenham uma taxa de captura acima de 100. Ordene os resultados decrescente pela taxa de captura.

```sql
select numero, nome, tipo1, tipo2, taxa_captura 
from pokemon
where tipo1 is not null and tipo2 is not null and taxa_captura > 100
order by taxa_captura desc
;
```

16. Quais são os tipos primários dos pokémons?

```sql
select distinct tipo1 from pokemon;
```

17. Selecione o `numero`, `nome` e `cor`; de todos os pokémons que o nome começa com a letra `D`.

```sql
select numero, nome, cor
from pokemon
where nome like "d%"
;
```

18. Qual é o pokémon mais poderoso de todas as gerações?

```sql
select *
from pokemon
where total = (select max(total) from pokemon)
;
```

19. Selecione o `numero`, `nome`, `defesa`, `ataque` dos pokémons com defesa > 60 e ataque <= 70; ordenados decrescente pelo `total`. 

```sql
select numero, nome, defesa, ataque
from pokemon
where defesa > 60 and ataque <= 70 
order by total desc
;
```

20. Selecione todos os pokémons do tipo `Planta` e `Venenoso` que não sejam `Green`, ordenado crescente pelo `nome`.

```sql
select *
from pokemon
where tipo1 like "planta" and tipo2 like "venenoso" and cor <> "green" 
;
```

21. Selecione de maneira crescente os nomes dos pokémons que possuem a letra y na 4ª posição do nome.

```sql
select *
from pokemon
where nome like "___y%" order by nome
;
```

22. Qual é o maior valor de `ataque_especial` cadastrado?

```sql
select *
from pokemon
where ataque_especial = (select max(ataque_especial) from pokemon)
;
```

23. Selecione o `numero`, `nome` e `altura_m` dos pokémons que possuem altura acima de 2,10m.

```sql
select numero, nome, altura_m 
from pokemon
where altura_m > 2.1
;
```

24. Quais são as diferentes tipos de cores dos pokémons? Apresente os resultados de maneira crescente pelo nome da cor.

```sql
select cor
from pokemon
group by cor 
order by cor
;
```

25. Selecione o `nome` e `velocidade` dos pokémons com velocidade entre 30 e 70. Ordene os resultados por nome (crescente) e velocidade (decrescente)

```sql
select nome, velocidade
from pokemon
where velocidade between 30 and 70 
order by nome asc, velocidade desc
;
```

26. Quem são os pokémons lendários? Apresente os resultados ordenados por `total` decrescente.

```sql
select *
from pokemon
where lendario = 1
order by total desc
;
```


27. Selecione os pokémons da primeira geração com taxa de captura igual a 255.

```sql
select *
from pokemon
where geracao = 1 and taxa_captura = 255
;
```


28. Quem é o mais poderoso? selecione o `Pikachu`, `Squirtle`, `Bulbasaur` e `Charmander`; ordenados decrescente pelo `total`. 

```sql
select * 
from pokemon
where nome like "pikachu" or 
nome like "squirtle" or 
nome like "bulbasaur" or 
nome like "charmander"
order by total desc
;
```

29. Quem são os pokémons da primeira geração, que começam com a letra `d` e não possuem tipo secundário?
Ordene os resultados crescente por `taxa_captura` e decrescente pelo `total`.

```sql
select * 
from pokemon
where geracao = 1 and nome like "d%" and tipo2 is null
order by taxa_captura asc, total desc
;
```

30. Qual é o ranking dos top 5 pokémons lendários com maior `taxa_captura` e `total`? Apresente apenas `numero, nome, total, taxa_captura` nos resultados.

```sql
select numero, nome, total, taxa_captura
from pokemon
where lendario = 1
order by taxa_captura, total asc
limit 5
;
```

31. Selecione o `numero`, `nome`, `peso_kg` dos pokémons com peso entre 2kg e 3kgs?

```sql
select numero, nome, peso_kg
from pokemon
where peso_kg between 2 and 3
;
```

32. Selecione o `numero`, `nome`, `tipo1` e `tipo2` dos pokémons com tipo primário `Normal`, que não possuem tipo secundário. Existe algum pokémon lendário nos resultados, se sim, os remova dos resultados?

```sql
select numero, nome, tipo1, tipo2
from pokemon
where tipo1 like "normal" and tipo2 is null and lendario = 0
;
```

33. Quem são os pokémons do tipo `Water` que não são azuis? Apresente `numero`, `nome`, `tipo1`, `tipo2` e `cor`, ordenados pelo `nome` de maneira crescente.

```sql
select numero, nome, tipo1, tipo2, cor 
from pokemon
where tipo1 like "water"
order by nome
;
```

34. Crie um ranking dos top 10 pokémons mais lentos.

```sql
select *
from pokemon
order by velocidade
limit 10
;
```

35. Selecione os pokémons cujo nome comece e termine com a letra `a`. 

```sql
select *
from pokemon
where nome like "a%"
;
```

36. Quem são os pokémons do tipo `Fire` que não são vermelhos? Apresente `numero`, `nome`, `tipo1`, `tipo2` e `cor`, ordenados pelo `nome` de maneira crescente.

```sql
select numero, nome, tipo1, tipo2, cor
from pokemon
where cor <> "red"
order by nome
;
```

37. Quais são os diferentes tipos de `peso_kg` dos pokémons? Apresente os resultados ordenados de maneira crescente.

```sql
select peso_kg
from pokemon
group by peso_kg
order by peso_kg
;
```

38. Selecione o `numero`, `nome` e `hp` dos pokémons com valores entre 0 e 100. Ordene os resultados de maneira crescente por `hp` e `nome`.

```sql
select numero, nome, hp
from pokemon
where hp between 0 and 100
order by hp, nome
;
```

39. Selecione o `numero`, `nome`, `hp`, `ataque`, `defesa` e `total`; dos pokémons com valores de `hp`, `ataque`, `defesa` maiores ou iguais a 100.

```sql
select numero, nome, hp, ataque, defesa 
from pokemon
where hp >= 100 and ataque >= 100 and defesa >= 100
;
```

40. Selecione todos os pokémons do tipos `Water` e `Gelo`, ordenados decrescente por `total`.

```sql
select * 
from pokemon
where tipo1 like "water" and tipo2 like "gelo" or tipo1 like "gelo" and tipo2 like "water"
order by total desc
;
```


## REFERÊNCIAS

* [Webiste Oficial - Pokémon](https://www.pokemon.com/br/guia-para-pais/)
* [Guia de Estilo SQL · SQL Style Guide](https://www.sqlstyle.guide/pt-br/)







