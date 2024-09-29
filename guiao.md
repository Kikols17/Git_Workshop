-> O que é o git?
	Todos já tivemos que fazer trabalhos de grupo, onde várias pessoas contribuem para o mesmo source code. Surgue imeadiatamente o problema de partilha de código do projeto. Muita gente neste caso recorre a metodos bastante arcaicos, como exemplo, enviar o mesmo ficheiro para trás e para a frente num grupo de Discord, ou então usar um google doc para que toda a gente tenha o projeto em dia. Obviamente tem que haver uma maneira mais fácil de partilhar código, manter um log de versões e assinalar as alterações entre cada versão e as contribuições de cada participante. o Git a ferramenta que toda industria usa, e resolve exatamente todos esses problemas.
	
    Para gerir um projeto, o git cria algo que se chama um repositório. Este está contido na pasta ".git", e pode ser local ou remoto. Um repo local é aquele que nós temos nas nossas máquinas locais, onde só nós conseguimos alterar. O repo remoto está num servidor algures na internet, onde toda a gente que tenha as credenciais para aceder consegue submeter commits.
    
    É para isto que servem serviços como o GitHub e o GitLab: sites que permitem aos seus utilizadores terem repositórios remotos, publicos ou privados, facilitando assim a gestão de grandes projetos com vários participantes. Estes serviços, como vamos demonstrar, oferecem tambêm outras features como "Issues" e diferentes níveis de permissões para aceder a branches.

	Uma coisa importante dos repositórios git, é que são basicamente bases de dados descentralizadas. Toda a gente que tem o repositório tem uma versão do estado do projeto da altura em que fez download (pull) da ultima vez. Deste modo, Nao importa se o repositorio é apagado do computador de um dos contribuidores ou até mesmo do servidor onde o repositório está a ser remotamente guardado, é sempre possível recupera-lo e redistribui-lo. A utilidade desta funcionalidade foi demonstrada pelo Gitlab quando em 2017 um dos funcionarios acidentalmente apagou nao só a base de dados principal e a de backup que continham todos os repositórios git, e tiveram que dar rollback para uma versão da base de dados 6 horas antes do incidente, nao estando portanto atualizada. Felizmente, apesar dos repositorios remotos não estarem atualizados, todos os projetos cujos membros tinham os seus repositórios locais em dia, conseguiram devolver os repos remotos ao seu estado mais atualizado apenas dando push. (para um reconto desta história: https://youtu.be/tLdRBsuvVKc)
	
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
    
    * git merge
        Por vezes é necessário reconsiliar dois branches com alterações incompatíveis. Para isso faze-mos "git merge" e escolhemos nas zonas problemáticas a versão que queremos que pervaleça.




-> Para o GITLAB/GITHUB
		- Criar um projeto do 0
		- Publicar um projeto local
		- Convidar contribuidores
            [Preciso powerpoint estar mais concreto para saber o que dizer melhor aqui, por causa dos visuais]

		- Gerir branches em grandes projetos
        - Gerir Pull Requests
		- Gerir "Issues"
            [A consultar para verificar com o stor de ES]