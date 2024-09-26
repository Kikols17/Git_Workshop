# Draft de workshop de GIT

pontos principais

	-> O que é o git?
   		- Sistema de Controlo de Versões Distribuído: O Git é uma ferramenta que permite rastrear alterações em arquivos de código ao longo do tempo,
		  ajudando a gerir diferentes versões de um projeto.
		- necessidade de version control em grandes projetos
		- explicar natureza descentralizada dos repositorios
		- explicar como o git guarda a diferença entre versões, em vez de guardar copias inteiras de ficheiros
		- diferença entre local repo e remote repo
		- explicar que GIT é uma ferramenta, e GITLAB e GITHUB são serviços de repositórios remotos
  	-> Vantagens do git:
    		- Colaboração Simplificada: Vários desenvolvedores podem trabalhar no mesmo projeto simultaneamente, sem sobrescrever o trabalho uns dos outros,
		  graças ao sistema de branches e merges.

    		- Histórico Completo de Alterações: O Git mantém um registo detalhado de todas as alterações feitas no projeto,
		  permitindo reverter para versões anteriores a qualquer momento.

    		- Velocidade e Eficiência: Por ser distribuído, cada colaborador tem uma cópia completa do repositório,
		  o que acelera as operações locais e minimiza as dependências de um servidor central.

    		- Integração com Plataformas de Hospedagem: Git integra-se facilmente com plataformas como o GitHub e o GitLab,
		  facilitando a partilha de código e a gestão de projetos colaborativos.
    
	-> Commandos git
		- apresentar comandos git, e como se usam na linha de comandos com exemplos
			* git init - Comando tem que ser executado no dir da pasta e serve para criar um repo git
			* git clone <URL-REPO> - Comando que cria uma cópia local de um repositório remoto.
			* git remote - Comando usado para gerir repositórios remotos. Pode listar, adicionar ou remover remotos.
			* git fetch - Comando que obtém as alterações mais recentes de um repositório remoto, mas não as aplica automaticamente.
			* git pull - Comando que obtém as alterações do repositório remoto e aplica-as ao repositório local (combinação de fetch e merge).
			* git add - Comando que adiciona ficheiros ao "staging", preparando-os para serem confirmados (committed).
			* git commit -m "Explicação" - Comando que cria um ponto no histórico do repositório, salvando as alterações adicionadas ao "staging".
			* git push - Comando que envia as alterações confirmadas (commits) do repositório local para o repositório remoto.
			* git diff - Comando que mostra as diferenças entre o código atual e as versões anteriores.
			* git log - Comando que exibe o histórico de commits do repositório, mostrando as mensagens e alterações feitas.
			* git merge - Comando que combina as alterações de uma branch noutra.


	-> Para o GITLAB/GITHUB
		- Criar um projeto do 0
		- Publicar um projeto local
		- Convidar contribuidores
		- Gerir branches em grandes projetos [A consultar para verificar com o stor de ES]
			* Boa pratica dita que cada "feature" que está a ser trabalhada, deve ser desenvolvida no ser próprio branch até estar pronta
			* Cada "equipa" deve trabalhar na sua "feature" numa pasta separada para evitar merge conflicts
		- Gerir Pull Requests
		- Gerir "Issues"
	

	-> DEMO?
		- [Se tivermos tempo, podemos ter uma demo preparada, um projeto no gitlab onde os participantes se juntam, criam os seus branches, fazem commits, e dão merge de volta, testando assim tudo o que foi dado]


	-> Ferramentas uteis
		- extenção de VSCODE
		- GITHUB GUI client
		- GITLAB GUI client
