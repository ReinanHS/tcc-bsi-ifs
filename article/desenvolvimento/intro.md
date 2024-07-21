# Desenvolvimento das melhorias

Para garantir que a ferramenta Limarka atendesse às necessidades dos alunos de maneira mais eficaz, foram implementadas diversas melhorias. Essas melhorias visaram aprimorar a estrutura do projeto, facilitar a configuração e o uso da ferramenta, além de integrar novas funcionalidades que aumentassem a eficiência no desenvolvimento de trabalhos acadêmicos. A seguir, detalhamos os principais aprimoramentos realizados.

## Fork e melhorias no Template

Com o objetivo de aprimorar a ferramenta Limarka, realizei o fork do projeto [abntex/trabalho-academico-limarka](https://github.com/abntex/trabalho-academico-limarka), criando o repositório [limarka-template-tcc](https://github.com/ReinanHS/limarka-template-tcc) no GitHub. Essa ação foi motivada pela necessidade de melhorar o modelo original e adicionar novas funcionalidades que pudessem ajudar os alunos a escreverem seus trabalhos acadêmicos com maior facilidade.

### Organização da estrutura de pastas

A estrutura de pastas original do modelo `abntex/trabalho-academico-limarka` era funcional, mas apresentava algumas limitações em termos de organização e facilidade de uso. No fork `limarka-template-tcc`, reorganizei as pastas de forma a tornar o projeto mais intuitivo para os usuários. Agora, os arquivos são distribuídos em diretórios específicos para cada tipo de conteúdo, como páginas, compilações, configurações e imagens, facilitando a navegação pelo projeto e a localização de arquivos específicos.

Veja a estrutura de cada diretório e suas respectivas funções:

- **.devcontainer**: Define o ambiente de desenvolvimento baseado em contêiner, facilitando a configuração em diferentes máquinas.
- **.github**: Inclui recursos importantes como templates para issues e pull requests, além de guias para contribuição.
- **.vscode**: Armazena configurações recomendadas para usuários do VS Code, como extensões e preferências de formatação.
- **build**: Diretório destinado aos outputs do processo de build, como PDFs gerados a partir do Markdown.
- **config**: Contém arquivos de configuração que determinam o comportamento de várias partes do projeto, como parâmetros de compilação.
- **docs**: Hospeda a documentação do projeto, que pode incluir manuais do usuário, especificações técnicas e guias de instalação.
- **imagens**: Repositório para as imagens utilizadas no documento, ajudando a organizar os recursos visuais.
- **pages**: Diretório que contém os arquivos markdow utilizadas no documento.
- **templates**: Armazena os templates LaTeX que definem a aparência e estrutura do documento final.

Graças a essa reorganização, colaboradores e usuários que buscam modificar, personalizar ou contribuir para o projeto encontrarão uma estrutura mais organizada e moderna em comparação a vários repositórios existentes no GitHub. Isso possibilita a configuração de diversos recursos dentro do projeto.

### Criação do diretório .vscode

A criação deste diretório permitiu adicionar várias configurações que facilitam o uso do projeto no Visual Studio Code, uma das ferramentas sugeridas na documentação para trabalhar com este repositório. Dentro deste diretório, foram configurados snippets, tasks e a sugestão de instalação de extensões que se integram ao projeto, facilitando a escrita dos trabalhos acadêmicos.

Quando o usuário abre o editor, essas configurações são automaticamente importadas, e as extensões necessárias são sugeridas para instalação. A Figura \ref{extensoes_mapeadas_vscode} demonstra como a sugestão é apresentada aos alunos ao abrirem o projeto no VSCode:

![Exemplificação da recomendação de instalação de extensões no VSCode](imagens/screenshot/extensoes-mapeadas-vscode.png){#extensoes_mapeadas_vscode escala=0.6}

Fonte: Autor.

As extensões mapeadas foram escolhidas por sua utilidade na escrita de documentos em Markdown, como a extensão **Brazilian Portuguese - Code Spell Checker**, responsável por corrigir erros de ortografia e concordância, e a extensão **Markdown Table Formatter**, que auxilia na criação e formatação de tabelas de forma correta e integrada aos snippets.

Outro detalhe importante adicionado ao modelo original é a configuração de uma task para realizar o build do documento pelo Limarka. No modelo original, os alunos precisariam digitar alguns comandos no terminal para compilar as informações no formato PDF. No entanto, isso poderia gerar um esforço adicional para o aluno, desviando seu foco da tarefa principal, que é a escrita do documento.

Para solucionar esse problema, foi criada uma configuração de task no VSCode, permitindo que a compilação do documento seja executada através de atalhos ou pressionando um botão na interface do VSCode. Essa configuração simplifica significativamente o processo de compilação, tornando-o mais acessível e permitindo que os alunos se concentrem na elaboração do conteúdo do seu trabalho acadêmico. A Figura \ref{limarka_builder_task} demonstra o processo de execução da task pela interface do VSCode:

![Exemplificação da execução da task de build para o Limarka](imagens/screenshot/limarka-builder-task.png){#limarka_builder_task escala=0.6}

Fonte: Autor.

Ao abrir a tela de tasks, que pode ser encontrada através do painel de terminal, o aluno encontrará uma lista de jobs disponíveis para execução dentro do editor. Utilizando as configurações do modelo disponibilizado, o aluno verá uma job chamada **Limarka Builder**. Ao selecionar essa opção, um terminal será aberto e todo o fluxo de build do documento será exibido, incluindo a geração do PDF. Caso ocorra algum erro, o aluno poderá visualizar as informações de erro diretamente no painel ou através dos logs armazenados na pasta de build.

### Criação do diretório build

Foi criada uma pasta exclusiva para a compilação dos resultados da ferramenta Limarka, separando os arquivos de build dos arquivos principais do projeto. Anteriormente, as informações de compilação ficavam na raiz do projeto, o que causava confusão. Com um diretório dedicado, todas as saídas de compilação são organizadas em um único local, melhorando a clareza e a manutenção do projeto. As vantagens de ter um diretório separado para compilação incluem:

- Facilita a limpeza e reconstrução do projeto sem interferir nos arquivos de origem.
- Melhora a organização, tornando mais fácil identificar e resolver problemas de build.
- Simplifica a integração com ferramentas de CI/CD, que podem focar diretamente no diretório de build.

### Criação do diretório .github

Este diretório foi criado para adicionar as configurações do [GitHub Actions](https://docs.github.com/pt/actions), integrando o projeto com pipelines de CI/CD. A integração com CI/CD é crucial para automatizar testes, builds e deploys, garantindo que o documento esteja sempre em um estado funcional. Além disso, centraliza templates de issues e pull requests, facilitando a contribuição e a manutenção do projeto.

### Criação do diretório .devcontainer

O diretório `.devcontainer` foi criado para configurar o [GitHub Codespaces](https://docs.github.com/pt/codespaces/overview). Esta configuração permite que os usuários desenvolvam e testem o projeto em um ambiente pré-configurado diretamente no navegador, eliminando a necessidade de configuração local. Isso proporciona uma experiência de desenvolvimento consistente e reduz problemas de compatibilidade entre diferentes ambientes de desenvolvimento.

### Criação do diretório pages

Este diretório foi criado para organizar arquivos específicos do projeto, como introduções e anexos. Além disso, serve para a compilação de páginas que são publicadas em um site estático no GitHub Pages pelo [limarka-render-html](https://github.com/ReinanHS/limarka-render-html), uma ferramenta desenvolvida para melhorar ainda mais a estrutura original do projeto. Com essa ferramenta, é possível compilar as informações em formato HTML, permitindo que sejam publicadas na internet e acessadas de maneira fácil.

A ferramenta `limarka-render-html` coleta as informações presentes no diretório `pages` seguindo regras estabelecidas no arquivo de configuração do projeto. Durante o processo de compilação no CI/CD, ela também realiza a compilação dessas informações em formato HTML.

![Exemplificação da página em HTML gerada pela ferramenta](imagens/screenshot/limarka-template-tcc-html.png){#limarka_template_tcc_html escala=0.4}

Fonte: Autor.

Observando a figura \ref{limarka_template_tcc_html}, podemos ver que a ferramenta faz o mapeamento do arquivo de configuração do projeto, extraindo informações como título, aluno, orientador e outros dados necessários para exibir um contexto geral sobre o documento. Além disso, a ferramenta disponibiliza um link para a visualização do documento compilado em PDF.

Ao utilizar a compilação nesse formato e a publicação na internet, os alunos conseguem compartilhar facilmente os resultados de seu trabalho com orientadores ou qualquer outra pessoa com acesso à internet. Isso permite que o trabalho do aluno seja visualizado diretamente pela internet, sem a necessidade de compilar as informações ou configurar o projeto em um computador local, uma vez que as informações estão publicamente disponíveis online.

O aluno também pode configurar a ferramenta para decidir se deseja ou não publicar as informações na internet. Dependendo das necessidades do aluno e de sua preferência quanto à exposição de seu trabalho, a publicação pode ser habilitada ou desabilitada nas configurações do CI/CD.

### Criação do diretório docs

Este diretório foi criado para seguir a filosofia "*documentação como código*" (docs as code). Nele, toda a documentação da ferramenta é mantida, incluindo manuais do usuário, especificações técnicas e guias de instalação. Os benefícios do docs as code incluem:

- Manutenção da documentação atualizada junto com o código, garantindo que as informações estejam sempre corretas e relevantes.
- Facilidade de contribuição, permitindo que desenvolvedores atualizem a documentação junto com as mudanças de código.
- Centralização de informações, tornando mais fácil para os usuários encontrar e entender as funcionalidades da ferramenta.

## Implementação da funcionalidade de importação de arquivos em Markdown

Com as melhorias na organização da estrutura de pastas, surgiu a necessidade de dividir o documento dentro dessa nova organização. No modelo original, o documento era escrito a partir do arquivo `trabalho-academico.md`, que continha todas as informações do documento a ser processado pela ferramenta Limarka. Dessa forma, os alunos precisavam escrever todo o conteúdo de seu TCC em um único arquivo, o que podia ser desorganizado e difícil de gerenciar.

No entanto, foi adicionada uma nova funcionalidade que realiza uma pré-compilação deste arquivo, possibilitando que os alunos façam a importação de outros arquivos em Markdown. Com essa nova estratégia, os alunos podem ter um arquivo separado para cada parte do seu documento, como um arquivo apenas para a introdução, outro apenas para o resumo e assim por diante. No final do processo, esses arquivos podem ser combinados no trabalho final através do arquivo `trabalho-academico.md`.

Essa abordagem não apenas melhora a organização do conteúdo, mas também facilita a colaboração, permitindo que diferentes partes do trabalho sejam desenvolvidas em paralelo. Cada seção ou capítulo pode ser escrita em um arquivo separado, que é posteriormente incluído no documento principal durante o processo de compilação.

Para importar um arquivo utilizando esta funcionalidade, os alunos devem fazer referência dentro do arquivo `trabalho-academico.md` usando a tag `@import('caminho do arquivo')`. Isso faz com que o pré-compilador, chamado de **limarka-help**, realize uma pré-compilação dos arquivos para dentro do `trabalho-academico.md` antes que o processo de compilação seja iniciado pela ferramenta Limarka. A Figura \ref{markdown_import_code} tem o exemplo do código para a importação de arquivos:

![Exemplo do bloco de código para a importação de arquivos](imagens/code/markdown-import-code.pdf){#markdown_import_code escala=0.8}

Fonte: Autor.

Ao aplicar essa estratégia de importação de arquivos Markdown no modelo original, diversos benefícios são proporcionados aos usuários do Limarka. A escrita modular e a organização aprimorada tornam o processo de elaboração de TCCs mais eficiente e menos propenso a erros. Além disso, a facilidade de colaboração e a clareza na estrutura do projeto contribuem para uma melhor experiência de uso.

## Repositório Docker

Para implementar as funcionalidades necessárias para a organização de pastas e importação de arquivos, foi necessário adicionar algumas customizações na imagem original da ferramenta Limarka. Essas customizações visavam garantir que a ferramenta suportasse as novas funcionalidades e fornecesse um ambiente consistente e atualizado para os usuários. Diante dessa necessidade, foi criado um repositório Docker específico para gerenciar essas modificações.

### Criação e automação do repositório limarka-docker

O repositório [limarka-docker](https://github.com/ReinanHS/limarka-docker) foi criado com o propósito de facilitar a manutenção e atualização das imagens Docker utilizadas pelo Limarka. Essa iniciativa permitiu a personalização do ambiente de desenvolvimento e execução, incorporando todas as dependências e configurações necessárias para suportar as novas funcionalidades implementadas.

Para garantir que as imagens Docker estivessem sempre atualizadas, foi automatizado o processo de construção e publicação das imagens. A automação foi configurada para gerar novas versões das imagens sempre que mudanças fossem feitas no repositório, garantindo que as melhorias e correções fossem rapidamente disponibilizadas aos usuários.

### Atualizações de segurança e publicação no Docker Hub

Manter as imagens Docker atualizadas é crucial para garantir a segurança e a estabilidade da ferramenta. No repositório [limarka-docker](https://github.com/ReinanHS/limarka-docker), foram implementadas automatizações que verificam e aplicam atualizações de segurança regularmente. Isso assegura que as imagens Docker estejam sempre protegidas contra vulnerabilidades e utilizem as versões mais recentes dos pacotes e dependências.

Além disso, as imagens Docker são publicadas no Docker Hub, facilitando o acesso e a utilização por parte dos alunos. A publicação no Docker Hub permite que as imagens sejam facilmente integradas em diferentes ambientes de desenvolvimento, tornando a configuração e o uso do Limarka mais acessíveis e eficientes.

### Integração das imagens Docker no limarka-template-tcc

A integração das imagens Docker no [limarka-template-tcc](https://github.com/ReinanHS/limarka-template-tcc) foi uma etapa crucial para garantir a consistência e a funcionalidade das novas melhorias implementadas. Utilizando as imagens Docker personalizadas, os alunos podem configurar rapidamente seu ambiente de desenvolvimento e execução, aproveitando todas as vantagens das novas funcionalidades sem a necessidade de configurações complexas.

Essa integração também garante que todos os usuários estejam utilizando a mesma versão da ferramenta, minimizando problemas de compatibilidade e facilitando a colaboração. A utilização das imagens Docker atualizadas e personalizadas assegura que o ambiente de desenvolvimento esteja sempre alinhado com as últimas melhorias e correções, proporcionando uma experiência de uso mais suave e eficiente.

## Integração com GitHub Codespaces

A integração do [limarka-template-tcc](https://github.com/ReinanHS/limarka-template-tcc) com o GitHub Codespaces foi uma etapa estratégica para tornar o desenvolvimento e a escrita de trabalhos acadêmicos ainda mais acessíveis e eficientes. O GitHub Codespaces oferece um ambiente de desenvolvimento completo no navegador, eliminando a necessidade de configurações locais.

### Configuração do template para uso no GitHub Codespaces

Para configurar o [limarka-template-tcc](https://github.com/ReinanHS/limarka-template-tcc) para uso no GitHub Codespaces, foram realizadas diversas adaptações no projeto. Primeiramente, foi necessário criar um diretório `.devcontainer` contendo os arquivos de configuração necessários para definir o ambiente de desenvolvimento.

Os arquivos de configuração no `.devcontainer` especificam a imagem Docker personalizada, garantindo que o ambiente de desenvolvimento no Codespaces seja idêntico ao utilizado localmente. A Figura \ref{devcontainer_config_json} apresenta um exemplo da configuração para o GitHub Codespaces:

![Exemplo da configuração para o GitHub Codespaces](imagens/code/devcontainer-config-json.pdf){#devcontainer_config_json escala=0.8}

Fonte: Autor.

Ao analisar a configuração, é possível observar que há uma referência à imagem criada no repositório Docker, na qual foram realizadas customizações para implementar as funcionalidades do novo modelo. Esse tipo de referência assegura que os alunos utilizem um ambiente já equipado com as ferramentas necessárias para executar o Limarka. Além disso, foram configurados scripts de inicialização que automatizam a configuração inicial, incluindo a instalação de extensões essenciais para o funcionamento do Limarka.

## DevOps e automação

A implementação de práticas de DevOps e automação foi essencial para aprimorar o fluxo de trabalho do projeto Limarka, tornando o processo de geração de documentos acadêmicos mais eficiente e robusto. Para alcançar esses objetivos, foram utilizadas pipelines no GitHub Actions, que automatizam tarefas críticas como a validação de arquivos Markdown, a geração de PDFs e a publicação de páginas HTML. A Figura \ref{github_action_limarka} ilustra o fluxo de execução da pipeline no GitHub Actions:

![Exemplificação do fluxo de execução da pipeline](imagens/screenshot/github-action-limarka.png){#github_action_limarka escala=0.6}

Fonte: Autor.

Com a compilação gerada por uma pipeline, os alunos podem ter seus documentos constantemente atualizados e publicados no GitHub Pages. Isso garante que a página HTML gerada contenha sempre o conteúdo mais atualizado disponível no repositório do GitHub.

### Implementação da Pipeline no GitHub Actions

A configuração da pipeline no GitHub Actions foi projetada para garantir a consistência e a qualidade dos documentos gerados pelo Limarka. A pipeline é acionada automaticamente sempre que há um push na branch `master`, iniciando uma série de jobs que verificam e processam o conteúdo do repositório.

#### Validação dos arquivos Markdown

O primeiro job, denominado `markdown-lint`, é responsável pela validação dos arquivos Markdown no repositório. Utilizando a ação `DavidAnson/markdownlint-cli2-action`, o job verifica se os arquivos Markdown estão em conformidade com as regras de formatação especificadas no arquivo `.markdownlint.yml`. Esta etapa é crucial para garantir a qualidade e a consistência do conteúdo antes de prosseguir para a compilação. A Figura \ref{markdown_lint_code} tem o exemplo do código em YAML para a configuração da job:

![Exemplo do bloco de código do markdown-lint](imagens/code/markdown-lint-code.pdf){#markdown_lint_code escala=0.8}

Fonte: Autor.

#### Compilação do documento com Limarka

O segundo job, `build-limarka`, realiza a compilação do documento utilizando a imagem Docker personalizada `reinanhs/limarka-help:1.0.0`. Este job executa comandos para verificar e compilar o documento, movendo os arquivos gerados para um diretório específico (`dist`). A etapa final deste job envolve o upload dos artefatos compilados para que possam ser utilizados em etapas subsequentes.

#### Geração automática do PDF e publicação no GitHub Pages

Após a compilação do documento, a próxima etapa envolve a geração de uma página HTML e a publicação do conteúdo no GitHub Pages. Este processo é gerido por dois jobs: `build-page` e `deploy`.

O job `build-page` depende da conclusão bem-sucedida do job `build-limarka`. Ele baixa os artefatos compilados e utiliza o `limarka-render-html` para gerar a versão HTML do documento. A estrutura HTML é então preparada para ser publicada, garantindo que todas as partes do documento estejam corretamente formatadas e prontas para visualização na web.

O job final de `deploy`, realiza a publicação do conteúdo gerado no GitHub Pages. Utilizando a action `JamesIves/github-pages-deploy-action`, esse job faz o deploy do diretório build para o GitHub Pages, tornando o documento acadêmico acessível pela internet. Esta etapa garante que a versão mais recente do documento esteja sempre disponível para visualização pública, facilitando o acesso e a disseminação do trabalho acadêmico.

## Documentação

Para facilitar o uso da ferramenta pelos alunos, a documentação original foi reescrita utilizando a metodologia Doc as Code. Essa abordagem garante que a documentação esteja sempre atualizada em relação ao modelo de template. Além disso, a nova documentação orienta os alunos sobre como utilizar os novos recursos implementados no modelo atualizado do template.

A documentação criada fornece referências abrangentes para todas as funcionalidades disponíveis na ferramenta, além de orientações sobre como configurar a ferramenta em diversos tipos de ambientes. A Figura \ref{limarka_template_docs} exemplifica a página da documentação disponível no [GitHub Pages](https://reinanhs.github.io/limarka-template-docs).

![Demonstração da página da documentação](imagens/screenshot/limarka-template-docs.png){#limarka_template_docs escala=0.6}

Fonte: Autor.

Ao acessar o [site da documentação](https://reinanhs.github.io/limarka-template-docs), os alunos encontrarão informações detalhadas sobre diversas funcionalidades da ferramenta. Além disso, a documentação possui um sistema de versionamento que acompanha a versão do repositório do GitHub do modelo. Isso garante que, se o modelo for atualizado ou uma funcionalidade for descontinuada, essas mudanças serão refletidas apenas na versão correspondente da documentação. As versões antigas continuarão oferecendo suporte e orientações sobre como a ferramenta era utilizada em versões anteriores.

### Metodologia Doc as Code

A metodologia Doc as Code é um paradigma que trata a documentação do software com a mesma importância e as mesmas práticas utilizadas no desenvolvimento de código. Isso significa que a documentação é escrita em formato de texto simples, como Markdown, e armazenada no controle de versão junto com o código-fonte. A documentação é gerida e atualizada usando as mesmas ferramentas e processos de desenvolvimento, como revisões de código, testes automatizados e integração contínua. Essa abordagem garante que a documentação evolua simultaneamente com o código, mantendo-se sempre relevante e precisa.

#### Criação do Repositório limarka-template-docs

Para implementar a filosofia da documentação como código de forma mais eficaz, foi criado o repositório `limarka-template-docs` no GitHub para gerenciar a publicação da documentação. Esse repositório segue a estrutura da ferramenta Docusaurus, uma solução popular para a geração de sites estáticos e de documentação. Com isso, foi criado o layout da documentação e configurada a sincronização da pasta de documentação do [repositório principal](https://github.com/ReinanHS/limarka-template-tcc) com esse repositório.

Essa sincronização é realizada através das versões publicadas, permitindo que a ferramenta baixe a versão, compile a documentação específica e a mescle com o layout presente nesse repositório. Após esse processo, a documentação é publicada no GitHub Pages. A figura \ref{limarka_template_docs_ci_cd} exemplifica o fluxo de execução do CI/CD nesse repositório:

![Demonstração do CI/CD para o limarka-template-docs](imagens/screenshot/limarka-template-docs-ci-cd.png){#limarka_template_docs_ci_cd escala=0.6}

Fonte: Autor.

Ao observar a imagem, é possível perceber que as informações são compiladas e processadas antes de serem publicadas na página do GitHub Pages. Isso garante que os alunos sempre encontrarão a documentação atualizada e consistente com o repositório principal.

#### Vantagens de manter a documentação atualizada junto com o código

Manter a documentação atualizada junto com o código oferece vários benefícios significativos para os alunos. Primeiramente, essa abordagem assegura que a documentação reflete as mudanças mais recentes no código, proporcionando aos alunos informações precisas e atualizadas sobre o uso da ferramenta. Isso elimina a frustração de seguir instruções desatualizadas e permite que os alunos aproveitem plenamente as últimas melhorias e correções.

Além disso, a documentação integrada com o ciclo de desenvolvimento facilita a aprendizagem contínua. À medida que novos recursos são adicionados ou modificados, os alunos podem acessar rapidamente a documentação relevante, sem necessidade de esperar por atualizações manuais. Essa sincronia entre código e documentação melhora a eficiência no aprendizado e na aplicação prática da ferramenta, garantindo uma experiência de usuário mais coesa e satisfatória.

### Aspectos cobertos pela documentação

A nova documentação que foi feita é abrangente e cobre todos os aspectos necessários para garantir que os usuários, desde iniciantes até colaboradores avançados, possam utilizar e contribuir com a ferramenta de forma eficiente. Ela está organizada em seções específicas que abordam desde a instalação inicial até funcionalidades avançadas, com exemplos práticos que facilitam o entendimento e a aplicação dos conceitos. A seguir, detalhamos os principais guias incluídos na documentação, cada um com seu foco particular para atender às necessidades de diferentes tipos de usuários.

#### Guia de instalação

Para ajudar os alunos a instalarem a ferramenta Limarka, foi criada uma seção abrangente denominada guia de instalação. Este guia visa proporcionar aos novos usuários uma compreensão completa de como configurar o Limarka em diferentes sistemas operacionais e ambientes de desenvolvimento. Além disso, foram desenvolvidos casos práticos de uso, mostrando exemplos reais de instalação e configuração.

A introdução à instalação oferece uma visão geral dos passos necessários para configurar o Limarka, garantindo que todos os requisitos sejam atendidos. São listadas as dependências essenciais como Docker, além de orientações sobre como instalá-las.

Para usuários do GitHub Codespace, o guia mostra como configurar rapidamente um ambiente de desenvolvimento no navegador, sem a necessidade de instalar nada localmente. São fornecidos passos detalhados para fazer um fork do repositório, configurar o Codespace e verificar a instalação do Limarka, garantindo que tudo esteja funcionando corretamente.

No Linux, o guia orienta os usuários pela instalação das dependências e do próprio Limarka. Os passos incluem a instalação do Docker. Exemplos práticos são fornecidos para verificar a instalação e realizar uma compilação de teste.

Para usuários do macOS, o guia detalha como utilizar o Homebrew para instalar as dependências necessárias. São fornecidos passos claros para configurar o ambiente e garantir que o Limarka esteja instalado corretamente. Exemplos práticos demonstram como verificar a instalação e compilar um documento.

No Windows, o guia aborda os passos adicionais necessários. São fornecidas instruções para a instalação do Docker. Exemplos práticos ajudam a verificar a instalação e realizar uma compilação de teste.

#### Guia para iniciantes

Para ajudar os alunos a iniciarem o uso da ferramenta Limarka, foi criada uma seção abrangente denominada guia para iniciantes. Este guia visa proporcionar aos novos usuários uma compreensão completa de como configurar, utilizar e compilar documentos com o Limarka. Além disso, foram desenvolvidos casos práticos de uso, mostrando exemplos reais de configurações e compilações.

O guia aborda a configuração inicial do Limarka, um passo essencial para garantir um ambiente de trabalho adequado. Os alunos são orientados sobre a instalação das dependências necessárias, clonagem do repositório e configuração dos arquivos essenciais, como o `configuracao.yaml`. Exemplos práticos são fornecidos para demonstrar como definir corretamente as opções do template, garantindo que todas as informações do TCC estejam bem configuradas.

A seção de compilação detalha como transformar o documento Markdown em um PDF formatado de acordo com as normas acadêmicas. O guia explica os passos necessários, desde a preparação do ambiente até a execução do comando `limarka build` para iniciar a compilação. Exemplos práticos ilustram o processo de criação de um documento simples e sua transformação em PDF.

O guia também apresenta o Playground, um ambiente de testes onde os alunos podem experimentar diferentes configurações e funcionalidades do Limarka sem afetar o projeto principal. As instruções mostram como criar um ambiente de testes, testar diferentes configurações e elementos de Markdown, e compilar os arquivos para verificar os resultados. Exemplos práticos demonstram como utilizar o Playground para experimentar com segurança.

#### Guia de elementos

Para ajudar os alunos a entender os elementos que a ferramenta Limarka dispõe, foi criada uma seção abrangente denominada guia de elementos. Este guia visa proporcionar aos alunos uma compreensão completa de todos os componentes disponíveis na ferramenta e como utilizá-los de maneira eficaz. Além disso, foram desenvolvidos casos práticos de uso, mostrando exemplos reais e como esses elementos se comportam após a compilação.

O guia aborda os parágrafos, que são a base de qualquer documento textual. Detalha como criar parágrafos bem estruturados no Limarka utilizando Markdown, garantindo clareza e coesão no texto. Exemplos práticos são fornecidos para demonstrar a criação de parágrafos simples e eficazes.

Também são discutidos os quadros, utilizados para destacar informações importantes ou fornecer exemplos detalhados. O guia oferece instruções sobre como criar quadros usando Markdown e HTML. Casos práticos ilustram como os quadros podem ser usados para organizar e apresentar dados de maneira clara.

A seção sobre tabelas ensina como criar tabelas utilizando a sintaxe Markdown, essenciais para a organização de dados de forma estruturada. Exemplos mostram a construção e formatação de tabelas para diferentes tipos de dados, e casos práticos demonstram sua aplicação em contextos acadêmicos.

No que diz respeito à citação de fontes, o guia explica como gerenciar bibliografias e referências utilizando Markdown e BibTeX, com exemplos detalhados de como citar fontes no texto e adicionar referências bibliográficas. Casos práticos evidenciam a importância de seguir os padrões acadêmicos.

As figuras, que são elementos visuais que complementam o texto e enriquecem o conteúdo do documento, também são cobertas. O guia fornece instruções sobre como inserir figuras utilizando a sintaxe Markdown, com exemplos que ilustram a adição de imagens e sua formatação adequada. Casos práticos mostram como figuras podem ser integradas ao texto para melhor compreensão.

Para organizar informações de maneira clara e fácil de ler, o guia explica como criar listas ordenadas e não ordenadas utilizando Markdown. Exemplos práticos mostram a criação e formatação de listas para diversos tipos de conteúdo.

Além disso, o guia detalha como escrever fórmulas em LaTeX e inseri-las diretamente no Markdown, com exemplos que demonstram a criação de equações complexas. Casos práticos mostram a aplicação das fórmulas em contextos científicos.

#### Guias avançados

Para ajudar os alunos e colaboradores a explorarem mais a fundo as capacidades do Limarka, foi criada uma seção abrangente denominada guias avançados. Este guia visa proporcionar uma compreensão detalhada de aspectos complexos do Limarka, como a arquitetura do template, a geração de sites estáticos e como contribuir para o projeto. Além disso, foram desenvolvidos casos práticos de uso, mostrando exemplos reais e como aplicar essas funcionalidades.

A seção sobre a arquitetura do template detalha a organização interna do projeto Limarka para trabalhos de conclusão de curso (TCC). Os alunos e colaboradores encontram uma descrição completa dos arquivos e diretórios que compõem o projeto, facilitando a compreensão da estrutura e a localização dos componentes. Isso é fundamental para quem deseja modificar, personalizar ou contribuir para o projeto. Exemplos práticos e uma árvore do projeto ajudam a visualizar e entender a organização do template.

A geração de sites estáticos é outra funcionalidade avançada abordada no guia. Este segmento da documentação explica como o Limarka integra automação de CI/CD para compilar o projeto e transformá-lo em um site estático em HTML, tornando-o acessível pela internet. São fornecidos detalhes sobre a configuração do arquivo destinado à geração de conteúdo estático, personalização das páginas HTML e implantação no GitHub Pages. Casos práticos ilustram o processo de configuração e publicação, promovendo uma forma inovadora e eficaz de compartilhar documentos acadêmicos online.

Por fim, o guia aborda como contribuir para o projeto, enfatizando a importância da colaboração para o desenvolvimento e aprimoramento de projetos de código aberto. Os alunos e colaboradores encontram informações sobre pré-requisitos para contribuição, como familiarizar-se com Git e a documentação do projeto, além de seguir o código de conduta. Instruções detalhadas mostram como criar um fork do repositório, clonar o fork, criar uma branch, fazer alterações, commit e push das mudanças, e finalmente, criar um pull request. Casos práticos e exemplos guiam os novos contribuidores através do processo, incentivando a participação ativa na comunidade do Limarka.
