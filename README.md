# ExerciciosMySQL
Exercícios MySQL envolvendo parte do comando SELECT. Esses exercícios pertecentem a aula **"Curso MySQL #12 - SELECT (Parte 2)", do curso MySQL, da plataforma de educação Curso em Vídeo.**

Para resolução destes exercícios, bem como acompanhemento geral do curso, é disponibilizado um arquivo DUMP contendo uma base de dados, disponível em: https://www.cursoemvideo.com/course/mysql/aulas/banco-de-dados/modulos/exercicio-para-curso-de-mysql/. (para fazer o download é necessário se cadastrar)

## Tabelas do banco de dados **cadastro**
![cursos-table](https://user-images.githubusercontent.com/76854209/125969519-e2f25488-51d0-49b4-9a87-9688db2dd383.jpg)
![gafanhotos-table](https://user-images.githubusercontent.com/76854209/125969912-1125636e-0c1c-4195-965f-b02c4fb157f9.jpg)

É válido dizer que algumas resoluções tem mais de uma resposta, a fim de compreender melhor o assunto.  

---
Link da aula: https://www.youtube.com/watch?v=q4hPo83-Buo 

Link para o curso: https://www.cursoemvideo.com/course/mysql

***
**Questões**
1) Uma lista com o nome de todos os gafanhotos Mulheres.
2) Uma lista com os dados de todos aqueles que nasceram entre 1/Jan/2000 e 31/Dez/2015.
3) Uma lista com o nome de todos os homens que trabalham como programadores.
4) Uma lista com os dados de todas as mulheres que nasceram no Brasil e que têm seu nome iniciando com a letra J.
5) Uma lista com o nome e nacionalidade de todos os homens que têm Silva no nome, não nasceram no Brasil e pesam menos de 100 Kg.
6) Qual é a maior altura entre gafanhotos Homens que moram no Brasil?
7) Qual é a média de peso dos gafanhotos cadastrados?
8) Qual é o menor peso entre os gafanhotos Mulheres que nasceram fora do Brasil e entre 01/Jan/1990 e 31/Dez/2000?
9) Quantas gafanhotos Mulheres tem mais de 1.90cm de altura?
***

**Resoluções**

1)
```
SELECT (nome) FROM gafanhotos WHERE sexo = 'F'
ORDER BY nome;
```
2)
```
SELECT * FROM gafanhotos WHERE nascimento BETWEEN '2000-01-01' AND '2015-12-31'
ORDER BY nascimento;
```
3)
```
SELECT nome, profissao FROM gafanhotos WHERE profissao = 'Programador'
ORDER BY nome;
```
4)
```
SELECT nome, nacionalidade FROM gafanhotos WHERE sexo = 'F' AND nacionalidade = 'Brasil' AND nome LIKE 'J%';

SELECT nome, nacionalidade FROM gafanhotos WHERE sexo = 'F' AND nacionalidade IN ('Brasil', 'Portugal', 'EUA')
ORDER BY nome;
```
5)
```
SELECT nome, nacionalidade FROM gafanhotos WHERE sexo = 'M' AND nacionalidade != 'Brasil' AND peso <100 AND nome LIKE '%Silva%'; 
```
6)
```
SELECT MAX(altura) FROM gafanhotos WHERE sexo = 'M' AND nacionalidade = 'Brasil'; 
 
SELECT nome, MAX(altura) FROM gafanhotos WHERE sexo = 'M' AND nacionalidade = 'Brasil'; 
```
7)
```
SELECT AVG(peso) FROM gafanhotos;
```
8)
```
SELECT MIN(peso) FROM gafanhotos WHERE sexo = 'F' AND nacionalidade != 'Brasil' AND nascimento BETWEEN '1990-01-01' AND '2000-12-31';
 
SELECT nome, MIN(peso) FROM gafanhotos WHERE sexo = 'F' AND nacionalidade != 'Brasil' AND nascimento BETWEEN '1990-01-01' AND '2000-12-31';
```
9)
```
SELECT COUNT(altura) FROM gafanhotos WHERE sexo = 'F' AND altura >'1.90';
```
