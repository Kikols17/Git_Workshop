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
--Fiz até aqui basicamente--

    Uma caracteristica interessante do git, é o modo como ele guarda versões. Obviamente ter uma cópia do projeto em cada versão seria muito dispendioso em termos de espaço. Seria quase como ter um monte de pastas chamadas "projeto_v1", "projeto_v2", "projeto_v3" e por ai a diante, onde cada pasta tem os mesmos ficheiros praticamente iguais, com apenas pequenas diferenças entre eles. Em vez disso, o git guarda apenas o que varia de uma versão para a outra. Deste modo, tudo o que uma versão nova tem que ter, é alguma maneira de indicar qual é a versão anterior, e quais são as diferenças da versão antiga para esta. (Um exemplo seria, "(ll5) -- ola bom dia" (ll5)"++ adeus boa noite"). Assim, para reconstruir um projeto a partir do log de versões git, partimos desde o primeiro commit, e avançamos versão a versão reconstruindo lentamente os ficheiros que estão no repo.


-> Comandos do git
	O git é uma ferramente de commandline. Nós vamos demonstrar como é que se aplica os comandos num terminal (que é o método aconselhado), mas se optarem por utilizar uma ferramenta GUI como aquelas que vamos demonstrar mais a frente, é uma transição fácil. A unica diferença é que em vez de escrever os comandos por extenço, são butões numa janela.

	* git init
		Para começar, vamos criar o nosso repositorio local. Há duas maneiras de fazer isto, init e clone. Começando com o init, criamos uma pasta nova, e abrimos o terminal nessa diretória. Escrevemos então "git init". Se virmos os ficheiros escondidos, podemos verificar que foi criada uma pasta chamada ".git". (um ficheiro escondido, é apenas um ficheiro cujo nome começa com ".") Nunca se deve mexer diretamente nos conteudos desta pasta. O nosso repositório está basicamente contido aqui, inclui portanto o log de todas as versões, e apenas o próprio programa git deve interagir com isto, para evitar apagar ou corromper o nosso repo.

	* git remote
		Depois de criar a nossa repo local, na maior parte das vezes queremos coloca-la num repositório remoto como o gitlab ou github. Para isso temos que ir a um desses sites, e criar um local para o nosso repositório. Depois voltamos ao nosso terminal, e informa-mos o git que este nosso repositório local tem um repo remoto tambem, e sempre que realizamos push ou pull, queremos faze-los relativamente a esse repositório. Para isso, escrevemos "git remote add origin <url>". Deste modo, o git sabe que este repo tem uma versão remota no url <url>, com o nome "origin". Para confirmar isso, podemos fazer "git remote get-url origin", que se o remote "origin" existir, escreve no ecrã o url a que este se refere, e onde se localiza o nosso remote repo.

	* git clone
		No entanto quando estamos a trabalhar em grupo, raramente somos nós a criar o repositório. Para isso existe o comando "git clone <url>", onde <url> refere-se a localização da repo remota que estamos a clonar. Ao fazer isto, é criada uma nova pasta com o nome da repo clonada, e abrindo-a, podemos ver todos os ficheiros que já foram commited, bem como mais uma vez a pasta ".git". Se mais uma vez fizermos "git remote get-url origin", podemos verificar que não precisamos de realizar "git remote add origin <url>", pois o git clone já tratou disso.

	* git pull
		O que acontece se o nosso repositório local está atrás do repositório remoto? Se alguem atualizar o remoto, temos que atualizar o nosso local. Para atualizar o nosso repo local, realizamos o comando "git pull". Este automaticamente vai ao repositório remoto, e atualiza o nosso local de modo a que este contenha as alterações feitas desde o ultimo pull. Se tivermos realizado alterações no repositório local, nao nos temos que preocupar, estas não serão perdidas ao realizar o pull, o git consegue conciliar estas versões automáticamente.

	* git add
		Como é que realizamos alterações aos nossos ficheiros na repo? Nao basta editar um ficheiro de texto e guarda-lo, precisamos de expecificar ao git que estas alterações façam parte de uma nova versão do projeto. O primeiro passo é adicionar as alterações ao "stage". Para isso, fazemos "git add <name_file>" para adicionar um ficheiro expecifico à stage, ou o mais comum, "git add ." que adiciona todas as alterções realizadas.
	
	* git commit
		Agora que temos as alterações na stage, precisamos de dar commit. "git commit -m "<mensagem>"" é usado para dar commit, sendo que o que seje "-m" é a mensagem deste commit. As mensagens de commit devem ser concisas e informativas relativamente ao que este commit faz. São elas que vão ajudar quem desenvolve e mantêm o projeto a saber o que cada commit alterou e contribuiu. (e são avaliadas a ES)

	* git push
		Finalmente temos o commit realizado com todas as alterações feitas. No entanto, se estamos a trabalhar num projeto com um remote repo, temos que atualizar essa tambêm. Isso pode ser feito com "git push". Este comando automáticamente atualiza o repositório remoto para refletir as alterções que nós realizamos.
		Por vezes, pode aparecer um erro do genero "failed to push some refs to ...". Se isto acontecer, quer dizer que alguêm atualizou o remote desde a ultima vez que demos push. Não há problema, basta fazermos "git pull --rebase" para por o nosso repo local ao nivel do remote, e depois correr o mesmo comando "git push" para que ambos local e remoto fiquem iguais e atualizados, nenhuma informação se perde.
		NUNCA se deve realizar NENHUM comando com a flag "-f" ou "--force", não só no comando "push". Se é preciso forçar o git a fazer algo, é porque algo não deveria estar a ser feito.
	
	* git log
		Para ver o historico dos commits numa repo, basta fazer "git log", q vemos a lista de commits, com as suas mensgens, datas, contribuidores, e branches.
	
	* git branch
		Como iremos explicar, por vezes é necessário dividir trabalho entre colaboradores, e queremos que ambos trabalhem no mesmo repositório paralelamente sem interferir um com o outro. Para isso utiliza-se o comando git branch para criar branches, que são basicamente realidades alternativas, começando a partir do commit de onde são criadas, e onde as alterações de um não afetam o outro.
	
	* git checkout
		Para viajar entre branches e versões antigas, utiliza-se o comando checkout. Basta escrever "git checkout <id>", sendo <id> o código do commit visível com "git log" ou "git status".
    
    * git merge
        Por vezes é necessário reconsiliar dois branches com alterações incompatíveis. Para isso faze-mos "git merge" e escolhemos nas zonas problemáticas a versão que queremos que pervaleça.




-> Para o GITLAB/GITHUB
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
