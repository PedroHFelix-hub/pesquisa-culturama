Pesquisa Culturama
Formulário de pesquisa desenvolvido com HTML e CSS, com foco em semântica, acessibilidade e SEO.

🔗 Acesse o formulário: https://pedrohfelix-hub.github.io/pesquisa-culturama/

Sobre o projeto
A Culturama é uma empresa fictícia que precisava de um formulário para coletar dados sobre os hábitos culturais do seu público. Os requisitos passados foram:

O formulário deve ser simples, funcional e responsivo
Tipografia definida: Fjalla One para títulos e Work Sans para textos
O projeto foi construído inteiramente com HTML e CSS, sem frameworks ou bibliotecas, e está publicado via GitHub Pages.

Contexto de aprendizado
Este projeto faz parte dos meus estudos no curso HTML e CSS: Formulários, SEO e acessibilidade da Alura.

De acordo com a ementa do curso, os objetivos de aprendizagem são:

Estruturar formulários HTML utilizando elementos semânticos
Validar dados com foco na experiência do usuário
Aplicar diretrizes de acessibilidade digital (WCAG e ARIA)
Utilizar ferramentas como Google Lighthouse e WAVE para avaliação de sites
Implementar estratégias de SEO técnico e de conteúdo para aprimorar a performance
O que foi implementado
Estrutura semântica
O formulário é dividido em seções agrupadas por <fieldset> e <legend>, que comunicam a relação entre os campos tanto visualmente quanto para tecnologias assistivas:

Seção	Conteúdo
Dados Pessoais	Nome, idade, data de nascimento, e-mail, telefone e foto de perfil
Perfil	Gênero, estado civil, estado e cidade
Hábitos	Redes sociais, estilo musical favorito e cor favorita
Satisfação	Grau de satisfação com a experiência
Feedback	Campo aberto para comentários
Consentimento	Aceite da LGPD e opt-in para receber os resultados
Tipos de campo e validação nativa
O projeto explora os tipos de input do HTML5 para aproveitar teclado adequado no mobile e validação sem JavaScript:

email, tel, date, number, color e file
min e max no campo de idade
required nos campos obrigatórios
radio para escolha única e checkbox para múltipla escolha
datalist no estilo musical — oferece sugestões sem impedir texto livre
<option value="" disabled selected> como placeholder nos selects, garantindo que o required funcione
Acessibilidade
Todo <label> vinculado ao seu campo por for/id, ampliando a área de clique e permitindo que leitores de tela anunciem cada controle corretamente
Agrupamento de controles relacionados com fieldset + legend
lang="pt-BR" declarado no documento
Texto alternativo na logo
Indicador de foco visível com :focus-visible, preservando a navegação por teclado
Hierarquia de títulos com um único <h1> por página
Validação com foco na experiência
O CSS usa a pseudo-classe :user-invalid em vez de :invalid. A diferença importa: :invalid marcaria os campos obrigatórios em vermelho já no carregamento da página, antes de qualquer interação — o formulário nasceria parecendo quebrado. Com :user-invalid, o erro só aparece depois que a pessoa interage com o campo ou tenta enviar.

SEO
<title> e <meta name="description"> descritivos
Estrutura de headings coerente
<meta name="viewport"> para responsividade
preconnect para o Google Fonts, reduzindo o tempo de carregamento das fontes
Responsividade
Construída com abordagem mobile-first:

Layout em coluna única com flex-direction: column nos fieldsets
Grupos de escolha organizados em grid, passando a duas colunas em telas maiores
Tipografia fluida com clamp(), dispensando media queries para o título
Container com max-width para manter a leitura confortável em telas grandes
Privacidade
O consentimento segue o princípio de finalidade específica da LGPD: o aceite obrigatório para o tratamento dos dados é separado do opt-in opcional para receber os resultados por e-mail — em vez de um único "aceito tudo".

Tecnologias
HTML5
CSS3 (variáveis, Flexbox, Grid, clamp(), :has(), :focus-visible, :user-invalid)
Google Fonts
Estrutura de arquivos
pesquisa-culturama/
├── imgs/
│   └── logo-culturama.png
├── culturama-favico.png
├── index.html
├── style.css
└── README.md
Como executar localmente
git clone https://github.com/PedroHFelix-hub/pesquisa-culturama.git
Depois é só abrir o index.html no navegador — o projeto não tem dependências nem etapa de build.

Aprendizados
Alguns pontos que ficaram mais claros durante o desenvolvimento:

name e id têm papéis diferentes. O name é o que identifica o campo no envio dos dados; o id é o que conecta o <label> ao controle. Precisar de um não dispensa o outro.
Campos de formulário não herdam a fonte do body. Sem font-family: inherit, os inputs continuam com a fonte padrão do navegador — e a identidade tipográfica se perde justamente dentro do formulário.
required em checkbox só funciona para um checkbox individual. Não existe forma nativa de exigir "pelo menos uma opção" de um grupo; isso depende de JavaScript.
Um fieldset aceita apenas um legend, e ele precisa ser o primeiro filho do grupo.
