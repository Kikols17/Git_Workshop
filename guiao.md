Boa Tarde, sejam bem-vindos ao **workshop de git**.

Hoje venho ensinar-vos os básicos do git e github/gitlab. Para começar, é importante dizer que Git e GitHub/GitLab não são a mesma coisa. Git é uma ferramenta de controlo de versões, enquanto que o GitHub e GitLab são plataformas onde podemos armazenar e partilhar o código que usamos com o Git.

Agora, vamos começar por focar-nos no Git. 
O Git foi criado em 2005 por Linus Torvalds, o criador do Linux, para resolver problemas que muitos de nós enfrentamos, como a partilha de código entre membros de um grupo. Provavelmente já se viram a trabalhar em projetos de grupo onde tinham de partilhar ficheiros de código através do WhatsApp ou Discord – um método complicado e propenso a erros. O Git foi criado exatamente para resolver isso.

Os principais objetivos do git são:

- Ser **Veloz**

- Ser um **projeto simples**

- Suportar o **desenvolvimento não-linear**: ou seja, várias partes de um projeto podem ser desenvolvidas em paralelo, sem interferirem umas com as outras.

- Ser **completamente distribuído**: ou seja, o Git permite que cada pessoa tenha uma cópia completa de todo o projeto, incluindo o histórico de todas as versões e alterações feitas.

-> Introduzir o exemplo:
        A utilidade desta funcionalidade foi demonstrada em 2017, quando um funcionário do GitLab acidentalmente apagou a base de dados principal e a de backup. Felizmente, como o Git é distribuído, muitos desenvolvedores tinham cópias locais atualizadas, o que permitiu restaurar os seus projetos para o estado mais recente.

Por último:

- É capaz de lidar com projetos grandes como é o caso do kernel linux(que é o núcleo do sistema operativo linux).

Atualmente o git é uma ferramenta bastante utilizada na industria, para terem uma ideia, 93% dos inquiridos numa sondagem de 2022 do Stack Overflow afirmaram usar Git. o que demonstra a importância desta ferramenta, tanto para a universidade como para o mercado de trabalho.
<https://survey.stackoverflow.co/2022/#version-control-version-control-system>

# Parte Prática do Workshop

-> Comandos do Git

- O Git é uma ferramenta que não contém uma interface gráfica, o que significa que os comandos são escritos num terminal. No entanto, existem ferramentas com interface gráfica que vou demonstrar mais à frente com o visual studio code.
### git init

Para começar, vamos criar o nosso repositório local, que nada mais é do que um projeto. Há duas maneiras de fazer isto: init e clone. Sendo o init um comando local e o clone um comando que se usa para ir buscar repositórios(ou projetos) ao github/gitlab. Começando com o init, criamos uma pasta nova e abrimos o terminal nesse diretório. Depois, escrevemos:

```bash

git init

```

  

Se virmos os ficheiros escondidos, podemos verificar que foi criada uma pasta chamada .git. Este diretório contém todo o log do repositório e não deve ser alterado manualmente pois é o Git que gere este conteúdo.

  

### git add .

Para realizar alterações aos nossos ficheiros, não basta editar um ficheiro de texto ou de código e guardá-lo; precisamos de informar o Git que essas alterações fazem parte de uma nova versão do projeto. O primeiro passo é adicionar as alterações ao staging(Que é uma etapa de confirmação). Para isso, fazemos:

```bash

git add <name_file>

```

  

Para adicionar um ficheiro específico ao stage, ou o mais comum:

```bash

git add .

```

  

Que adiciona todas as alterações realizadas.

  

---

### git commit -m "mensagem"

Agora que temos as alterações no stage, precisamos de fazer um commit. O comando:

```bash

git commit -m "<mensagem>"

```

Onde o -m se refere à mensagem do commit. As mensagens devem ser concisas e informativas sobre o que foi alterado. Elas ajudam a equipa a entender o que cada commit fez, contribuindo para o desenvolvimento do projeto.(vale também a pena mencionar que são avaliadas a ES)

  

Para acedermos ao histórico de Versões podemos utilizar o comando:

  

### git log

  

Para ver o histórico de versões utilizamos este comando, onde podemos retirar a hash dos commits para voltar atrás no código utilizando o comando:

  

---

  

### git checkout 'hash do commit'

  

Este comando volta para o estado do commit indicado pela hash

  

---

**Fazer demonstração voltando atrás numa alteração feita**

  
  

## Parte Remote do git

  

Todos os comandos que mencionei até agora são locais, ou seja, são para projetos individuais que ficam armazenados no nosso computador.

Mas quando estamos a trabalhar em equipa, com outros colegas, queremos todos ter o mesmo repositório no mesmo estado e é aqui que entra uma plataforma como o github. Tudo o que vou falar para o github serve também para o gitlab mas neste workshop vamos só trabalhar com o github pois o processo de criação de conta é mais simples no github. Bem para começar, o primeiro passo é configurar as credenciais para quando formos executar comandos que façam alterações no servidor não termos de colocar o Username e o token todas as vezes.
- Aceder ao site
- Explicar o processo
- Criar um ficheiro de texto no desktop
- Formato 'https://'username':'token'@github.com'
- Comando do git: 
```bash
git config --global credential.helper "store --file ~/Desktop/Git_credential.txt"
```
Posto isto. O nosso primeiro passo é clonar o repositório remoto para o nosso ambiente local. Ou seja, ir buscar o repositório ao github. Para isso, usamos o comando:


### git clone 'url'

  

Este comando faz uma cópia completa do repositório remoto para o nosso computador, incluindo o histórico de commits e todos os ficheiros. Assim que o repositório é clonado, podemos começar a fazer as nossas alterações no código localmente.
	Se o repositório for privado, para clonar é necessário estar como colaborador do mesmo. Mas como este é público não é preciso

	
Agora que já temos o repositório clonado e podemos trabalhar no projeto, é importante lembrar que após fazermos as nossas alterações e confirmá-las com git commit, também precisamos de sincronizar essas alterações com o repositório remoto, para que os membros ou os líderes das equipas possam ver as nossas mudanças.
Para isso damos:

### git push

  

O comando consiste em enviar essas mudanças para o repositório remoto, de forma a manter o projeto atualizado e disponível para os outros colaboradores. Para isso, utilizamos o comando:

  
```bash
git push
```
  

O comando git push atualiza automaticamente o repositório remoto, refletindo todas as alterações que fizemos localmente.


### git pull

Após nós enviarmos as alterações para o servidor, os restantes colaboradores precisam de atualizar o seu repositório, e por isso usamos o comando:

  

```bash

git pull

```

  

Este comando obtém as alterações do repositório remoto e atualiza o nosso repositório local. Se tivermos alterações locais, o Git irá conciliar automaticamente as versões, preservando as nossas alterações e adicionando as do remoto.


**Erro comum no push**:

Se aparecer uma mensagem como *"failed to push some refs to..."*, significa que alguém atualizou o repositório remoto desde a última vez que fizemos pull. Para resolver, basta fazer pull. E tentar outra vez. O mesmo erro pode aparecer caso as alterações num único push exceda os limites de tamanho: Que são 100MB
   

**Nota importante**:

Nunca se deve usar o comando com as flags `-f` ou `--force` (como em `git push --force`), pois isso significa que estamos a forçar o Git a fazer algo que normalmente não deveria ser feito. Forçar operações no Git pode resultar em perda de dados ou conflitos graves.

  

## Parte dos branches:

  

Depois de entender como trabalhamos com repositórios locais e remotos é importante perceber que, muitas vezes, não estamos a trabalhar diretamente na branch principal, mas sim em branches separadas.

  

As Branches são uma ferramenta que nos permite trabalhar em funcionalidades, correções ou testes isolados, sem afetar o código principal até estarmos prontos para integrar as nossas alterações. Para perceber melhor essa parte vamos então observar a seguinte imagem. (depois de explicar minimamente a imagem do francisco) vamos então explorar os comandos mais importantes para gerir branches.

  

## Comandos de Branches
Para criar um branch utilizamos o comando:

### git branch 'nome_do_branch'

  

Este comando cria uma nova branch que aponta para o commit mais recente. O que pode ser útil quando queremos começar a trabalhar numa nova funcionalidade sem afetar o código atual.

  

---

  

### git checkout 'nome_do_branch'

  

Este comando permite alternar para uma branch existente, ou no nosso exemplo, recém criada. Para que possamos trabalhar nela.

  

---

Acho que vale a pena referir que a partir da versão 2.23, para se criar e alternar para essa branch, recém criada. Se pode utilizar logo o comando:

  

### git switch -c 'nome_do_branch'

  

---

## Para gerirmos Branches Locais e Remotas

  

Renomear uma branch local:

  

### git branch --move 'nome_antigo' 'novo_nome'

  

Se quiseres alterar o nome de uma branch local, usa-se este comando. É útil para corrigir nomes de branches sem criar novas.

  

Mas para atualizarmos a branch num repositório remoto já temos que utilizar:

  

### git push --set-upstream origin 'novo-nome'

  

Este comando atualiza o repositório remoto com a nova branch ou as mudanças feitas ao nome da branch local.

  

Para eliminarmos uma branch no repositório remoto podemos usar:

  

### git push origin --delete 'antigo-nome'

  

Para apagar uma branch remota, utilizamos este comando, geralmente depois de ter feito merge ou de a branch já não ser necessária.

  

---

## Merge de Branches

  

Depois de termos feito as alterações na nossa branch e estivermos prontos para integrar o nosso trabalho na branch principal(ou na dev), precisamos de fazer o merge. Para isso, usamos:

  

### git merge 'nome-branch'

  

O comando git merge combina as alterações da branch especificada com a branch atual. Quando duas pessoas fazem alterações ao mesmo podem existir conflitos. E agora na Demo vamos observar isso mesmo.
- Conflitos podem ser resolvidos no visual studio

---

-> **Para o GITLAB/GITHUB**
	O Github e Gitlab, como já referimos, são sites de hosting de repos, mas têm tambêm algumas funcionalidades que ajudam o desenvolvimento. São praticamente identicos em features. O GitLab é considerado o preferido das grandes empressas, é open-source, e é pago (felizmente com o programa alunos, é possível criar conta gratuita com o mail da UC). O GitHub é o mais utilizado e considerado mais acessível, e como é propriedade da microsoft, ganha dinheiro da pior maneira possível: a maneira do costume, utilizando as repos para treinar o Copilot. É tambêm notável de dizer que com o mail da UC no site do GitHub é possível conseguir o Copilot de graça, mas pela minha experiencia não consigo recomendar a sua utilização para mais do que trabalhos extremamente simples. [Depois muda isto, dado que és tu que vais dizer, dá a tua recomendação, esta é apenas a minha]

		- Criar um projeto do 0
			Vamos agora criar agora um projeto do 0. Basta abrir o site do github/gitlab e seguir estes passos.
			[SEE /prints dir]

		- Publicar um projeto local
			-> GitHub: agora que temos o projeto criado, temos duas opções: podemos começar mesmo do 0, correndo os comandos de cima, ou importar para a remote repo um projeto que já temos na nossa máquina, corremos os comandos de baixo.
			-> Gitlab: No caso do gitlab, similarmente, basta verificarmos o README.md, e correr o commando que queremos conforme o que queremos fazer.

		- Convidar contribuidores
			[Vou fazer uns gifs disto para por no powerpoint em loop, n há muito que dizer]
		

		- Gerir branches em grandes projetos
			Uma grande parte de gerir um projeto git, é saber como gerir uma equipa com muitas pessoas. No caso do trabalho de Engenharia de Software que muito estão agora a fazer é uma equipa de 30 pessoas, mas numa grande empressa ou projeto open-source podem estar milhares de pessoas envolvidas. Para facilitar a organização, o standard de industria é divídir os contribuidores em equipas, onde cada um recebe tarefas de um Team Leader, que por sua vez recebe tarefas do Project Manager. Agora surge um problema, porque como todas as equipas estão a trabalhar basicamente em "features" ou bugs diferentes em paralelo, é necessário separar os seus trabalhos. Entram aqui os Branches. Por defeito existe sempre um branch "main", que é considerado o "autorativo", e que tem que estar sempre a funcionar. A partir dele costuma-se dar branch, e cria-se um branch "dev", onde serão feitas alterações em preparação para a nova versão do software, que só é merged para "main" quando se tem a certeza que tudo funciona e que está pronto a entrar em produção. O Project Manager é responsável por gerir estes dois branches. Depois, dentro de "dev" cada equipa é responsável por criar um branch, com o nome da feature em que está a trabalhar, onde irá colocar todos os commits até a feature estar pronta. Cada Team Leader é responsável por gerir este seu branch. Depois disso, cada contribuidor, quando lhe for atribuido trabalho, deve fazer um branch, a partir do branch da sua equipa, onde faz alterações até o seu trabalho estar completo, para depois dar merge para o branch da feature, com autorização do Team Leader.

        - Gerir Pull Requests
			Como já dissemos, diferentes tipos de participantes no projeto têm diferentes obrigações e branches para gerenciar. Desta maneira, a funcionalidade do projeto que está em cada branch pode ser gerido com Pull Requests. Para dar merge de um branch para outro, é necessário colocar um Pull Request, que o gerente desse branch tem que aceitar, para o pull ser realizado. Deste modo, os Team Leaders conseguem garantir que todo o código que compoe a feature da sua equipa está de acordo com os requerimentos, e o Product Manager que todo o código no branch de "dev" e "main" está funcional.

		- Gerir "Issues"
			Para gerir um grande nível de contribuidores, respeitar deadlines, e manter o projeto focado, são utilizadas Issues. Estas são basicamente tarefas TODO, que o Product Manager cria e delega aos Team Leaders abaixo dele. Depois, os Team Leaders partem as Issues em tarefas mais pequenas, e destribuem nas pelos contribuidores das suas equipas.
            [A consultar para verificar com o stor de ES]
