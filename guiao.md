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

**Parte Prática do Workshop**

-> Comandos do Git
	- O Git é uma ferramenta que não contém uma interface gráfica, o que significa que os
 comandos são escritos num terminal. No entanto, existem ferramentas com interface gráfica, que vamos demonstrar mais à frente.
### `git init`
	Para começar, vamos criar o nosso repositório local. Há duas maneiras de fazer isto: init e clone. Começando com o init, criamos uma pasta nova e abrimos o terminal nesse diretório. Depois, escrevemos:
 
```bash
git init
```
	Se virmos os ficheiros escondidos, podemos verificar que foi criada uma pasta chamada .git. Este diretório contém todo o log do repositório e não deve ser alterado manualmente. É o Git que gere este conteúdo.

### `git clone`
	No entanto, quando estamos a trabalhar em grupo, raramente somos nós a criar o repositório. Para isso, existe o comando git clone <url>, onde <url> refere-se à localização do repositório remoto que estamos a clonar.

### `git clone <url>`

	Ao fazer isto, é criada uma nova pasta com o nome do repositório clonado, e podemos ver todos os ficheiros já 
"committed". Se fizermos git remote get-url origin, podemos verificar que não precisamos de realizar git remote add origin <url>, pois o git clone já tratou disso.

### `git add .`
	Como é que realizamos alterações aos nossos ficheiros no repositório? Não basta editar um ficheiro de texto e guardá-lo; precisamos de informar o Git que essas alterações fazem parte de uma nova versão do projeto. O primeiro passo é adicionar as alterações ao staging. Para isso, fazemos:
```bash
git add <name_file>
```

Para adicionar um ficheiro específico ao stage, ou o mais comum:
```bash
git add .
```

Que adiciona todas as alterações realizadas.

---
### `git commit -m "mensagem"`
	Agora que temos as alterações no stage, precisamos de fazer um commit. O comando:
```bash
git commit -m "<mensagem>"
```
Onde o -m refere-se à mensagem do commit. As mensagens devem ser concisas e informativas sobre o que foi alterado. Elas ajudam a equipa a entender o que cada commit fez, contribuindo para o desenvolvimento do projeto.(São avaliadas a ES)

---
### `git push`
	Depois de fazermos o commit com todas as alterações, se estivermos a trabalhar num projeto com um repositório remoto, precisamos de **atualizar também o repositório remoto**. Isto é feito com o comando:

```bash
git push
```

Este comando atualiza automaticamente o repositório remoto para refletir as alterações que realizámos localmente.

**Erro comum**:  
Se aparecer uma mensagem como *"failed to push some refs to..."*, significa que alguém atualizou o repositório remoto desde a última vez que fizemos push. Para resolver, basta utilizar:


### `git pull`
	Se o nosso repositório local estiver **desatualizado** em relação ao repositório remoto, usamos o comando:

```bash
git pull
```

Este comando obtém as alterações do repositório remoto e atualiza o nosso repositório local. Se tivermos alterações locais, o Git irá conciliar automaticamente as versões, preservando as nossas alterações e adicionando as do remoto.

---

**Nota importante**:  
Nunca se deve usar o comando com as flags `-f` ou `--force` (como em `git push --force`), pois isso significa que estamos a forçar o Git a fazer algo que normalmente não deveria ser feito. Forçar operações no Git pode resultar em perda de dados ou conflitos graves.

---

### `git merge`
	Por vezes, é necessário reconciliar duas branches com alterações incompatíveis. Para isso, usamos o comando:

```bash
git merge
```

Durante o merge, o Git mostrará as zonas problemáticas (conflitos), e podemos escolher manualmente quais as alterações que devem prevalecer.

---
### `git remote`
	Depois de criar a nossa repo local, na maior parte das vezes queremos coloca-la num repositório remoto como o gitlab ou github. Para isso temos que ir a um desses sites, e criar um local para o nosso repositório. Depois voltamos ao nosso terminal, e informa-mos o git que este nosso repositório local tem um repo remoto tambem, e sempre que realizamos push ou pull, queremos faze-los relativamente a esse repositório. Para isso, escrevemos "git remote add origin <url>". Deste modo, o git sabe que este repo tem uma versão remota no url <url>, com o nome "origin". Para confirmar isso, podemos fazer "git remote get-url origin", que se o remote "origin" existir, escreve no ecrã o url a que este se refere, e onde se localiza o nosso remote repo.
---

### Comandos com Branches

- **Criar uma nova branch**:
    ```bash
    git branch <nome>
    ```
    Este comando cria uma nova branch que aponta para o commit mais recente.

- **Mudar para uma branch existente**:
    ```bash
    git checkout <nome-branch>
    ```
    Este comando permite trocar de branch.

- **Criar e mudar para uma nova branch (a partir da versão 2.23)**:
    ```bash
    git switch -c <nome-branch>
    ```
    Com este comando, podemos criar e mudar para uma nova branch em apenas uma linha. Para voltar à branch anterior:
    ```bash
    git switch -
    ```

- **Renomear uma branch local**:
    ```bash
    git branch --move <antigo-nome> <novo-nome>
    ```
    Este comando altera o nome de uma branch localmente.

- **Atualizar a branch no repositório remoto**:
    ```bash
    git push --set-upstream origin <novo-nome>
    ```
    Para refletir a mudança de nome no repositório remoto, devemos fazer push.

- **Eliminar uma branch no repositório remoto**:
    ```bash
    git push origin --delete <antigo-nome>
    ```

---

### Tarefas Adicionais após Alterar o Nome de uma Branch:
Se alterares o nome de uma branch importante, deves realizar algumas tarefas extra para garantir que tudo funciona corretamente:
1. Atualizar projetos que dependem desse repositório.
2. Ajustar ficheiros de configuração de runners de teste.
3. Modificar scripts de build e release.
4. Redirecionar configurações no repositório, como a branch padrão ou regras de merge.
5. Atualizar referências ao nome antigo da branch na documentação.
6. Fechar ou fazer merge de *pull requests* que estejam a usar a branch antiga.

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
