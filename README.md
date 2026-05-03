# 🔐 Caderno Temático: Segurança em APIs REST

![Status](https://img.shields.io/badge/status-concluído-success)
![Foco](https://img.shields.io/badge/foco-API%20Security-blue)
![Ferramenta](https://img.shields.io/badge/ferramenta-NotebookLM-orange)
![Nível](https://img.shields.io/badge/nível-intermediário%20→%20avançado-purple)

> 🎓 **Desafio de Projeto — DIO** | Explorando o NotebookLM como Ferramenta de Estudo Ativo

---

## 📑 Sumário

- [Contexto e Objetivos](#-contexto-e-objetivos)
- [Curadoria de Fontes](#-curadoria-de-fontes)
- [Engenharia de Prompts e Aprendizados](#-engenharia-de-prompts-e-aprendizados)
- [Conexão com a Prática](#-conexão-com-a-prática)
- [Miniguia de Estudo](#-miniguia-de-estudo)
- [Glossário](#-glossário)
- [Prompts Reutilizáveis](#-prompts-reutilizáveis)
- [Reflexão Final](#-reflexão-final)

---

## 📌 Contexto e Objetivos

Escolhi estudar **segurança em APIs REST** porque já utilizo APIs no dia a dia, mas percebi que minha visão ainda estava muito focada em *fazer funcionar*, não necessariamente em *fazer seguro*.

Na prática, eu implementava autenticação com JWT e consumia APIs normalmente, mas sempre ficava a dúvida:

> *"Isso está realmente seguro ou só está funcionando?"*

Esse projeto surgiu dessa necessidade de aprofundar o conhecimento e entender os riscos reais que acontecem em produção. A maioria dos tutoriais trata autenticação como um detalhe, "adiciona um JWT aqui e tá resolvido". Não está.

### 🎯 Objetivos

| # | Objetivo |
|---|----------|
| 1 | Entender os principais vetores de ataque com base no **OWASP API Security Top 10** |
| 2 | Diferenciar autenticação, autorização e controle de acesso na prática |
| 3 | Aplicar boas práticas de **JWT**, **OAuth 2.0** e **refresh token rotation** |
| 4 | Compreender rate limiting, validação de entrada e logging seguro |
| 5 | Criar um material de referência reutilizável para o dia a dia |

---

## 📚 Curadoria de Fontes

Priorizei documentação oficial e RFCs em vez de artigos de blog, material que não fica desatualizado em seis meses.

| # | Fonte | Descrição | Link |
|---|-------|-----------|------|
| 1 | **OWASP API Security Top 10** | Os 10 riscos mais críticos em APIs. Referência central da área. | [owasp.org](https://owasp.org/www-project-api-security/) |
| 2 | **JWT.io Introduction** | Estrutura, assinatura e casos de uso de JSON Web Tokens. | [jwt.io/introduction](https://jwt.io/introduction) |
| 3 | **RFC 6749 — OAuth 2.0** | Especificação oficial do protocolo. Consultei os fluxos Authorization Code e Client Credentials. | [rfc-editor.org](https://www.rfc-editor.org/rfc/rfc6749) |
| 4 | **NIST SP 800-63B** | Guia de identidade digital do NIST, com foco em tokens e gestão de sessões. | [pages.nist.gov](https://pages.nist.gov/800-63-3/sp800-63b.html) |
| 5 | **Mozilla Web Security Guidelines** | Headers HTTP de segurança, CORS, HTTPS e políticas de conteúdo. | [infosec.mozilla.org](https://infosec.mozilla.org/guidelines/web_security) |

> 💡 O NotebookLM se destacou na **síntese entre fontes**: conseguiu cruzar OWASP, NIST e RFC 6749 numa mesma resposta sem eu precisar abrir cada documento manualmente.

---

## 🧪 Engenharia de Prompts e Aprendizados

Essa seção documenta a evolução real dos prompts, incluindo o que não funcionou e por quê.

---

### Rodada 1 — Pergunta aberta demais

```
Me explica tudo sobre segurança em APIs.
```

**Resultado:** Resposta genérica. O NotebookLM fez um resumo superficial, sem aprofundar em nada.

> ❌ **Aprendizado:** Prompts abertos geram respostas rasas. Sem escopo definido, a ferramenta não sabe onde aprofundar.

---

### Rodada 2 — Adicionando contexto e exemplo

```
Com base nas fontes carregadas, explica o que é BOLA (Broken Object Level Authorization)
e por que ele é considerado o risco #1 do OWASP API Top 10.
Me dá um exemplo prático de como isso aparece em código.
```

**Resultado:** Muito melhor, conceito explicado com citação direta da fonte.

> ⚠️ **Cicatriz:** O código veio com sintaxe inconsistente (misturou frameworks).
> ✅ **Correção:** Sempre especificar linguagem e framework ao pedir código.

---

### Rodada 3 — Comparação entre fontes

```
Compara autenticação e autorização com base nas minhas fontes.
Onde cada uma delas aborda essa distinção?
```

**Resultado:** Excelente. O NotebookLM cruzou OWASP, NIST e JWT.io com ângulos distintos, foi quando percebi o real valor da ferramenta como sintetizador de múltiplas fontes.

> ✅ **Aprendizado:** Pedir comparação entre fontes é o uso mais poderoso do NotebookLM.

---

### Rodada 4 — Geração de material de estudo

```
Cria um glossário com os 15 termos mais importantes de segurança em APIs REST.
Para cada termo, escreve uma definição curta (2-3 linhas) e indica de qual fonte ele veio.
```

**Resultado:** Glossário bem organizado, com alguns termos muito similares entre si.

> ⚠️ **Cicatriz:** O NotebookLM às vezes "conecta" fontes que não se relacionam de fato.
> ✅ **Correção:** Pedir sempre o trecho ou página exata da fonte. Isso reduz alucinações significativamente.

---

### Rodada 5 — Teste de profundidade técnica

```
Explica o fluxo de Refresh Token Rotation de forma detalhada.
Quais são os riscos se isso for implementado errado?
Usa o RFC 6749 e o OWASP como base.
```

**Resultado:** Sólido, cobriu riscos de token replay e race conditions em rotações concorrentes.

> 💡 **Dica:** Para RFCs extensos, enviar só a seção relevante como documento separado melhora muito a qualidade da resposta.

---

### 🗺️ Mapa de Evolução

```
Pergunta aberta          →  resultado raso
        ↓
Adicionar contexto       →  melhor, mas código inconsistente
        ↓
Especificar linguagem    →  código correto
        ↓
Comparar entre fontes    →  síntese de alto valor
        ↓
Pedir trecho exato       →  reduz alucinações
```

---

## 🧩 Conexão com a Prática

Grande parte dos problemas de segurança não acontece por falta de tecnologia, acontece por **decisões simples feitas errado**.

### Erros comuns em projetos reais

| Erro | Consequência |
|------|-------------|
| Confiar no frontend para validação | Qualquer requisição direta à API bypassa a validação |
| Não validar autorização no backend | Usuário acessa dados de outros usuários |
| Tratar autenticação como "resolvido" | JWT sem validação de expiração ou com segredo fraco |
| Ausência de rate limiting em login | Força bruta viável sem esforço |
| Tokens sem rotação | Token roubado vira acesso permanente |

> A autenticação diz **quem você é**. A autorização diz **o que você pode fazer**. Confundir os dois, ou só implementar um, é a origem de boa parte dos incidentes reais.

---

## 📖 Miniguia de Estudo

### 1. OWASP API Security Top 10

Os três riscos mais críticos, responsáveis pela maioria dos incidentes reais:

#### 🔴 API1 — Broken Object Level Authorization (BOLA)
A API não verifica se o usuário tem permissão para acessar *aquele objeto específico*.

```python
# ❌ Vulnerável — qualquer usuário logado pode trocar o ID
@app.get("/orders/{order_id}")
def get_order(order_id: int, current_user: User = Depends(get_current_user)):
    return db.get_order(order_id)  # Não valida se order pertence ao current_user

# ✅ Correto — verifica propriedade do recurso
@app.get("/orders/{order_id}")
def get_order(order_id: int, current_user: User = Depends(get_current_user)):
    order = db.get_order(order_id)
    if order.user_id != current_user.id:
        raise HTTPException(status_code=403, detail="Acesso negado")
    return order
```

#### 🔴 API2 — Broken Authentication
Falhas nos mecanismos de autenticação: tokens com expiração longa, ausência de rotação de refresh tokens, senhas sem política mínima, sem bloqueio por tentativas excessivas.

#### 🟠 API3 — Broken Object Property Level Authorization
Variação do BOLA no nível dos campos. Um usuário pode alterar propriedades que não deveria, como modificar seu próprio `role` para `admin` via PATCH.

> Os riscos de API4 a API10 cobrem: consumo excessivo de recursos, autorização por função quebrada, mass assignment, configurações incorretas, gestão de inventário de APIs e consumo inseguro de APIs de terceiros.

---

### 2. JWT — Estrutura, Assinatura e Armadilhas

Um JWT tem três partes separadas por pontos: `header.payload.signature`

```
eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VyMTIzIiwiZXhwIjoxNzAwMDAwMDAwfQ.assinatura
      HEADER                          PAYLOAD                          SIGNATURE
```

**Armadilhas mais comuns:**

| Problema | Consequência |
|----------|-------------|
| `alg: none` aceito | Token sem assinatura é válido |
| Segredo fraco no HS256 | Força bruta do segredo é viável |
| Não validar `exp` | Tokens expirados continuam funcionando |
| JWT no `localStorage` | Vulnerável a ataques XSS |
| Sem refresh token rotation | Token roubado = acesso permanente |

**Refresh Token Rotation:** a cada uso do refresh token, ele é invalidado e um novo é emitido. Se o token antigo reaparecer (sinal de roubo), toda a família de tokens é revogada.

---

### 3. OAuth 2.0 — Fluxos Principais

OAuth 2.0 é um framework de **autorização delegada**, não autenticação (isso é papel do OpenID Connect).

| Fluxo | Quando usar |
|-------|------------|
| **Authorization Code + PKCE** | Aplicações com usuário humano |
| **Client Credentials** | Comunicação máquina-a-máquina (M2M) |

**Boas práticas:**
- `access_token`: vida curta (15min a 1h)
- `refresh_token`: vida longa, mas **rotacionado a cada uso**
- Nunca expor `client_secret` no frontend

---

### 4. Headers HTTP de Segurança

| Header | Proteção |
|--------|----------|
| `Strict-Transport-Security` | Força HTTPS |
| `X-Content-Type-Options: nosniff` | Previne MIME sniffing |
| `X-Frame-Options: DENY` | Previne clickjacking |
| `Content-Security-Policy` | Controla recursos carregáveis |
| `Referrer-Policy` | Controla dados no header Referer |

> Para APIs JSON puras, HSTS e X-Content-Type-Options são sempre recomendados. CSP tem menos relevância sem HTML.

---

### 5. Rate Limiting

Protege contra abuso, scraping e força bruta.

| Estratégia | Quando usar |
|-----------|------------|
| Por IP | Simples, mas contornável com rotação de IPs |
| Por usuário autenticado | Mais eficaz para usuários logados |
| Por endpoint | Endpoints sensíveis (login, reset de senha) exigem limites mais restritivos |

**Resposta correta:**
```http
HTTP/1.1 429 Too Many Requests
Retry-After: 60
```

> Rate limiting e account lockout são **complementares**, não substitutos.

---

## 📘 Glossário

| Termo | Definição |
|-------|-----------|
| **Autenticação** | Verificação de *quem é* o solicitante (ex: login com senha, token). |
| **Autorização** | Verificação de *o que* o solicitante tem permissão de fazer ou acessar. |
| **BOLA** | Broken Object Level Authorization — falha em validar se o usuário pode acessar o objeto específico requisitado. |
| **JWT** | JSON Web Token — formato compacto para transmitir claims de forma verificável por assinatura. |
| **Access Token** | Token de curta duração usado para acessar recursos protegidos. |
| **Refresh Token** | Token de longa duração usado para obter novos access tokens sem nova autenticação. |
| **Refresh Token Rotation** | Prática de invalidar o refresh token a cada uso e emitir um novo. |
| **OAuth 2.0** | Framework de autorização delegada — permite que um app acesse recursos em nome de um usuário. |
| **PKCE** | Proof Key for Code Exchange — extensão do OAuth 2.0 que protege o Authorization Code Flow contra interceptação. |
| **Rate Limiting** | Restrição ao número de requisições que um cliente pode fazer em um período de tempo. |
| **CORS** | Cross-Origin Resource Sharing — controla quais origens podem acessar uma API. |
| **HSTS** | HTTP Strict Transport Security — instrui o browser a usar apenas HTTPS. |
| **Mass Assignment** | Vulnerabilidade onde campos inesperados de uma requisição são atribuídos diretamente a um objeto. |
| **Throttling** | Técnica para limitar a taxa de processamento de requisições, evitando sobrecarga. |
| **Claim** | Par chave-valor no payload de um JWT com informações sobre o token ou portador. |
| **Scope** | No OAuth 2.0, define o nível de acesso solicitado/concedido ao client. |
| **Bearer Token** | Padrão onde quem possui o token tem acesso, sem verificação adicional de identidade. |
| **API Gateway** | Camada intermediária que centraliza autenticação, rate limiting e roteamento de APIs. |

---

## 🔁 Prompts Reutilizáveis

Prompts que funcionaram bem e podem ser adaptados para outros temas:

**Entender um conceito novo:**
```
Explica [conceito] com base nas fontes carregadas.
Usa uma analogia simples primeiro, depois aprofunda no aspecto técnico.
Cita o trecho exato da fonte onde isso é abordado.
```

**Identificar riscos práticos:**
```
Quais são os principais vetores de ataque relacionados a [conceito/tecnologia]?
Para cada um: como o ataque funciona, como detectar e como mitigar.
Usa as fontes carregadas e indica a origem de cada informação.
```

**Comparar abordagens:**
```
Compara [abordagem A] com [abordagem B] em segurança, complexidade de implementação
e casos de uso recomendados. Se mais de uma fonte aborda isso, mostra como cada uma vê.
```

**Gerar exemplos de código:**
```
Me dá um exemplo prático de implementação de [conceito] em [linguagem/framework].
Destaca os pontos onde a segurança é crítica e o que acontece se forem ignorados.
O exemplo deve refletir boas práticas, não apenas o mínimo funcional.
```

**Criar material de revisão:**
```
Com base nas fontes, cria 10 perguntas de revisão sobre [tema], do nível básico ao avançado.
Inclui a resposta esperada e qual fonte suporta aquela resposta.
```

**Consolidar aprendizado:**
```
Resume os 5 pontos mais importantes sobre [tema] com base nas nossas conversas e fontes.
Identifica lacunas, algo que as fontes mencionam mas que não ficou claro nas discussões.
```

---

## 🧭 Reflexão Final

Usar o NotebookLM como ferramenta de estudo ativo foi bem diferente de simplesmente ler documentos. A virada aconteceu quando parei de fazer perguntas genéricas e passei a tratar a ferramenta como um **interlocutor técnico**, alguém que leu os mesmos textos e pode ajudar a sintetizar, comparar e aprofundar.

As "cicatrizes" documentadas aqui são, na minha opinião, a parte mais valiosa deste projeto:

> **Erro que você registra vira aprendizado. Erro que você não registra vira o mesmo problema semana que vem.**

---

*Projeto desenvolvido como parte do desafio da [DIO](https://www.dio.me/) — Explorando o NotebookLM como Ferramenta de Estudo Ativo.*
