# 🔐 Caderno Temático: Segurança em APIs REST

> **Desafio de Projeto - DIO | Explorando o NotebookLM como Ferramenta de Estudo Ativo**

---

## Sumário

- [Contexto e Objetivos](#-contexto-e-objetivos)
- [Curadoria de Fontes](#-curadoria-de-fontes)
- [Engenharia de Prompts e Cicatrizes](#-engenharia-de-prompts-e-cicatrizes)
- [Miniguia de Estudo](#-miniguia-de-estudo)
  - [Resumos Estruturados](#resumos-estruturados)
  - [Glossário](#glossário)
  - [Prompts Reutilizáveis](#prompts-reutilizáveis)

---

## 📌 Contexto e Objetivos

Escolhi **segurança em APIs REST** como tema porque é uma área que me interessa muito na prática. Trabalho com desenvolvimento de aplicações que consomem e expõem APIs, e percebi que boa parte dos tutoriais que encontro por aí trata autenticação e autorização como algo secundário, quase um "vamos adicionar um JWT aqui e tá resolvido". Não tá.

Queria entender de verdade os mecanismos por trás, os vetores de ataque mais comuns e como pensar em segurança desde o design da API, não só no final.

**Objetivos do estudo:**

- Entender os principais vetores de ataque em APIs REST (com base no OWASP API Security Top 10)
- Compreender na prática as diferenças entre autenticação, autorização e controle de acesso
- Aprender boas práticas de implementação de JWT, OAuth 2.0 e refresh token rotation
- Revisar conceitos de rate limiting, validação de entrada e logging seguro
- Montar um material de referência que eu possa consultar no futuro durante o desenvolvimento

---

## 📚 Curadoria de Fontes

Selecionei 5 fontes abertas focadas em conteúdo técnico e prático. Todas foram enviadas para o NotebookLM em PDF ou lidas via link.

| # | Fonte | Descrição | Link |
|---|-------|-----------|------|
| 1 | **OWASP API Security Top 10 (2023)** | Documento oficial da OWASP com os 10 riscos mais críticos em APIs. É a referência da área, denso, mas muito rico. | [owasp.org](https://owasp.org/www-project-api-security/) |
| 2 | **JWT.io Introduction** | Explicação detalhada sobre o funcionamento de JSON Web Tokens: estrutura, assinatura e casos de uso. | [jwt.io/introduction](https://jwt.io/introduction) |
| 3 | **The OAuth 2.0 Authorization Framework (RFC 6749)** | RFC oficial do protocolo OAuth 2.0. Pesado, mas consultei os fluxos de Authorization Code e Client Credentials. | [rfc-editor.org](https://www.rfc-editor.org/rfc/rfc6749) |
| 4 | **NIST SP 800-63B — Digital Identity Guidelines** | Guia do NIST sobre autenticação e gestão de credenciais. Usei especialmente a seção sobre tokens e sessões. | [pages.nist.gov](https://pages.nist.gov/800-63-3/sp800-63b.html) |
| 5 | **Mozilla Web Security Guidelines** | Guia prático da Mozilla sobre headers HTTP de segurança, CORS, HTTPS e políticas de conteúdo. | [infosec.mozilla.org](https://infosec.mozilla.org/guidelines/web_security) |

> **Por que essas fontes?** Priorizei documentos oficiais e RFCs em vez de artigos de blog porque queria material que não ficasse desatualizado em 6 meses. O NotebookLM se saiu bem com PDFs técnicos, conseguiu cruzar informações entre fontes sem eu precisar abrir cada uma manualmente.

---

## 🧪 Engenharia de Prompts e Cicatrizes

Aqui está o que realmente aprendi sobre como usar o NotebookLM de forma estratégica, incluindo as tentativas que não funcionaram bem.

---

### Rodada 1 — Pergunta inicial (muito aberta)

**Prompt testado:**
> *"Me explica tudo sobre segurança em APIs."*

**Resultado:**
Resposta genérica demais. O NotebookLM basicamente fez um resumo superficial das fontes, sem aprofundar em nada. Parecia um sumário executivo que eu mesmo teria escrito sem ajuda.

**O que aprendi:** Prompts abertos demais geram respostas rasas. Preciso delimitar escopo, público-alvo e nível de detalhe esperado.

---

### Rodada 2 — Refinando com contexto

**Prompt testado:**
> *"Com base nas fontes que eu carreguei, explica o que é BOLA (Broken Object Level Authorization) e por que ele é considerado o risco #1 do OWASP API Top 10. Me dá um exemplo prático de como isso aparece em código."*

**Resultado:**
Muito melhor. O NotebookLM citou o documento da OWASP diretamente, explicou o conceito com clareza e deu um exemplo de endpoint vulnerável. A resposta foi rastreável, deu pra ver exatamente de onde cada trecho veio.

**Cicatriz:** O exemplo de código que ele gerou misturou Python com uma sintaxe meio inventada. Tive que pedir explicitamente para gerar em FastAPI/Python puro. Anotei: *sempre especificar a linguagem/framework quando pedir código.*

---

### Rodada 3 — Comparação entre conceitos

**Prompt testado:**
> *"Compara autenticação e autorização com base nas minhas fontes. Onde cada uma dessas fontes aborda essa distinção?"*

**Resultado:**
Aqui o NotebookLM brilhou. Ele cruzou o OWASP, o NIST e o JWT.io na mesma resposta, mostrando como cada um aborda o tema com um ângulo diferente. Foi quando percebi o real valor da ferramenta, não é só um chatbot, é um sintetizador de múltiplas fontes.

---

### Rodada 4 — Gerando material de estudo

**Prompt testado:**
> *"Com base em tudo que você tem acesso, cria um glossário com os 15 termos mais importantes de segurança em APIs REST. Para cada termo, escreve uma definição curta (2-3 linhas) e indica de qual fonte ele veio."*

**Resultado:**
Gerou um glossário bem organizado. Alguns termos ficaram com definições muito similares entre si (ex: "token" e "access token"), então fiz uma rodada de refinamento pedindo para diferenciar melhor.

**Cicatriz:** Percebi que o NotebookLM às vezes "inventa" conexões entre fontes que não existem de fato — ele sugere que fonte A confirma algo que só a fonte B menciona. Passei a pedir sempre: *"cita a página ou trecho exato da fonte."* Isso reduziu bastante as alucinações.

---

### Rodada 5 — Teste de profundidade

**Prompt testado:**
> *"Explica o fluxo de Refresh Token Rotation de forma detalhada. Quais são os riscos se isso for implementado errado? Usa o RFC 6749 e o OWASP como base."*

**Resultado:**
Resposta detalhada e tecnicamente sólida. Ele apontou os riscos de token replay e race conditions em rotações concorrentes — coisas que eu sabia existir mas não tinha formalizado.

**Dificuldade encontrada:** O RFC 6749 é muito extenso e o NotebookLM às vezes se perdia entre seções. Tive mais sucesso quando enviei só a seção relevante do RFC como um documento separado.

---

### Mapa de Evolução dos Prompts

```
Pergunta aberta → resultado raso
   ↓
Adicionar contexto + delimitar escopo → melhor, mas código genérico
   ↓
Especificar linguagem/framework + pedir citação de fonte → bom
   ↓
Pedir comparação entre fontes → excelente para síntese
   ↓
Pedir trecho exato da fonte → reduz alucinações significativamente
```

---

## 📖 Miniguia de Estudo

### Resumos Estruturados

---

#### 1. Os 10 Riscos Mais Críticos em APIs (OWASP API Security Top 10)

O OWASP API Security Top 10 é atualizado periodicamente e representa um consenso da comunidade de segurança sobre onde as APIs mais falham. Os três primeiros são responsáveis pela maioria dos incidentes reais:

**API1 — Broken Object Level Authorization (BOLA)**
Acontece quando a API não verifica se o usuário autenticado tem permissão para acessar *aquele objeto específico*. Exemplo clássico: `GET /api/pedidos/1234`, e qualquer usuário logado consegue trocar o `1234` por qualquer outro ID e ver dados alheios. A autenticação existe, mas a autorização por objeto está ausente.

**API2 — Broken Authentication**
Falhas nos mecanismos de autenticação: tokens com expiração muito longa, ausência de rotação de refresh tokens, senhas sem política mínima, ausência de bloqueio por tentativas excessivas.

**API3 — Broken Object Property Level Authorization**
Variação do BOLA, mas no nível dos campos. O usuário pode atualizar propriedades que não deveria — como mudar seu próprio `role` para `admin` numa requisição PATCH.

**API4 — Unrestricted Resource Consumption**
Ausência de rate limiting adequado. APIs sem limites de requisição são alvos fáceis para ataques de força bruta, scraping e DDoS na camada de aplicação.

**API5 — Broken Function Level Authorization**
Endpoints administrativos acessíveis por usuários comuns. Geralmente aparece quando a API diferencia usuários só pelo frontend, mas não valida permissões no backend.

> Os riscos de API6 a API10 cobrem: mass assignment, falhas de segurança no servidor, configurações incorretas, gestão inadequada de inventário de APIs e consumo inseguro de APIs de terceiros.

---

#### 2. JWT — Estrutura, Assinatura e Armadilhas

Um JWT é composto por três partes separadas por pontos: `header.payload.signature`

- **Header:** algoritmo de assinatura (ex: `HS256`, `RS256`) e tipo do token
- **Payload:** claims — informações sobre o usuário e metadados do token (ex: `sub`, `iat`, `exp`, `roles`)
- **Signature:** garante integridade — não que o conteúdo seja secreto, mas que não foi alterado

**Armadilhas comuns:**

| Problema | Consequência |
|----------|-------------|
| Usar `alg: none` | Token aceito sem validação de assinatura |
| Segredo fraco no HS256 | Força bruta do segredo é viável |
| Não validar `exp` | Tokens expirados continuam funcionando |
| Guardar JWT no localStorage | Vulnerável a XSS |
| Não usar refresh token rotation | Token roubado vira acesso permanente |

**Refresh Token Rotation** é a prática de invalidar o refresh token a cada uso e emitir um novo. Se o token antigo aparecer de novo (indicando que foi roubado), a família inteira de tokens é invalidada.

---

#### 3. OAuth 2.0 — Fluxos Principais

O OAuth 2.0 não é um protocolo de autenticação (isso é o OpenID Connect), mas sim de *autorização delegada*. Os fluxos mais relevantes para APIs:

**Authorization Code Flow (+ PKCE)**
Usado quando há um usuário humano. O client recebe um `code` de curta duração e troca por um `access_token`. O PKCE (Proof Key for Code Exchange) protege contra interceptação do código.

**Client Credentials Flow**
Para comunicação máquina-a-máquina (M2M). O client autentica diretamente com `client_id` + `client_secret` e recebe um token. Não há contexto de usuário.

**Importante:** `access_token` deve ter vida curta (15min a 1h). `refresh_token` pode ter vida longa, mas *deve* ser rotacionado a cada uso.

---

#### 4. Headers HTTP de Segurança

Headers que toda API deveria incluir nas respostas:

| Header | Para que serve |
|--------|---------------|
| `Strict-Transport-Security` | Força HTTPS |
| `X-Content-Type-Options: nosniff` | Previne MIME sniffing |
| `X-Frame-Options: DENY` | Previne clickjacking |
| `Content-Security-Policy` | Controla quais recursos podem ser carregados |
| `Referrer-Policy` | Controla informações no header Referer |

Para APIs JSON puras (sem HTML), o CSP tem menos relevância, mas HSTS e X-Content-Type-Options são sempre recomendados.

---

#### 5. Rate Limiting e Throttling

Rate limiting protege contra abuso, scraping e força bruta. Estratégias comuns:

- **Por IP:** mais simples, mas fácil de contornar com rotação de IPs
- **Por usuário autenticado:** mais eficaz para usuários logados
- **Por endpoint:** endpoints sensíveis (login, recuperação de senha) devem ter limites mais restritivos

Respostas adequadas: `429 Too Many Requests` com header `Retry-After` informando quando tentar novamente.

**Account lockout** após N tentativas de login falhas é complementar ao rate limiting — não substituto.

---

### Glossário

| Termo | Definição |
|-------|-----------|
| **Autenticação** | Processo de verificar *quem é* o solicitante (ex: login com senha, token). |
| **Autorização** | Processo de verificar *o que* o solicitante tem permissão de fazer ou acessar. |
| **BOLA** | Broken Object Level Authorization — falha em validar se o usuário tem acesso ao objeto específico requisitado. |
| **JWT** | JSON Web Token — formato compacto para transmitir claims entre partes de forma verificável por assinatura. |
| **Access Token** | Token de curta duração usado para acessar recursos protegidos. |
| **Refresh Token** | Token de longa duração usado para obter novos access tokens sem nova autenticação. |
| **Refresh Token Rotation** | Prática de invalidar o refresh token a cada uso, emitindo um novo a cada rotação. |
| **OAuth 2.0** | Framework de autorização delegada que permite que um app acesse recursos em nome de um usuário. |
| **PKCE** | Proof Key for Code Exchange — extensão do OAuth 2.0 que protege o Authorization Code Flow contra interceptação. |
| **Rate Limiting** | Restrição ao número de requisições que um cliente pode fazer em um período de tempo. |
| **CORS** | Cross-Origin Resource Sharing — mecanismo que controla quais origens podem acessar uma API. |
| **HSTS** | HTTP Strict Transport Security — header que instrui o browser a usar apenas HTTPS. |
| **Mass Assignment** | Vulnerabilidade onde campos não esperados de uma requisição são atribuídos diretamente a um objeto do sistema. |
| **Throttling** | Técnica para limitar a taxa de processamento de requisições, evitando sobrecarga. |
| **Claim** | Par chave-valor dentro do payload de um JWT que carrega informações sobre o token ou seu portador. |
| **Scope** | No OAuth 2.0, define o nível de acesso solicitado/concedido ao client. |
| **Bearer Token** | Padrão de autenticação via token onde quem possui o token (`Bearer`) tem acesso — sem verificação adicional de identidade. |
| **API Gateway** | Camada intermediária que centraliza autenticação, rate limiting e roteamento para uma ou mais APIs. |

---

### Prompts Reutilizáveis

Esses prompts funcionaram bem durante meu estudo e podem ser adaptados para revisões futuras ou para estudar outros temas de segurança:

---

**Para entender um conceito novo:**
```
Explica [conceito] com base nas fontes carregadas. 
Usa uma analogia simples primeiro, depois aprofunda no aspecto técnico.
Cita o trecho exato da fonte onde isso é abordado.
```

---

**Para identificar riscos práticos:**
```
Quais são os principais vetores de ataque relacionados a [conceito/tecnologia]?
Para cada um, descreve: como o ataque funciona, como detectar e como mitigar.
Usa as fontes carregadas como base e indica a origem de cada informação.
```

---

**Para comparar abordagens:**
```
Compara [abordagem A] com [abordagem B] em termos de segurança, complexidade de implementação e casos de uso recomendados.
Se mais de uma fonte aborda isso, mostra como cada uma enxerga a comparação.
```

---

**Para gerar exemplos de código:**
```
Me dá um exemplo prático de implementação de [conceito] em [linguagem/framework].
Destaca os pontos onde a segurança é crítica e o que acontece se eles forem ignorados.
O exemplo deve refletir boas práticas, não apenas o mínimo funcional.
```

---

**Para criar material de revisão:**
```
Com base nas fontes, cria [5/10/15] perguntas de revisão sobre [tema], do nível básico ao avançado.
Inclui a resposta esperada para cada pergunta e qual fonte suporta aquela resposta.
```

---

**Para consolidar aprendizado:**
```
Resume os 5 pontos mais importantes que aprendi sobre [tema] com base nas nossas conversas e nas fontes.
Identifica qualquer lacuna — algo que as fontes mencionam mas que não ficou totalmente claro nas nossas discussões.
```

---

## 🧭 Reflexão Final

Usar o NotebookLM como ferramenta de estudo ativo foi uma experiência bem diferente de apenas ler documentos. A grande virada foi parar de fazer perguntas genéricas e começar a tratar a ferramenta como um interlocutor técnico — alguém que leu os mesmos textos que eu e pode ajudar a sintetizar, comparar e aprofundar.

As "cicatrizes" documentadas aqui são, na minha opinião, a parte mais valiosa deste projeto. Erro que você registra vira aprendizado. Erro que você não registra vira o mesmo problema semana que vem.

---

*Projeto desenvolvido como parte do desafio da [DIO](https://www.dio.me/) — Explorando o NotebookLM como Ferramenta de Estudo Ativo.*
