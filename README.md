# 🛡️ Guía rápida: PentAGI — pentesting autónomo con agentes, solo con autorización (ES · PT)

> 📚 **Colección / Coleção**: esta hoja forma parte de [cheatsheets](https://github.com/Ezra-Zhao/cheatsheets) — 100 hojas de referencia en un solo repositorio. / Esta folha faz parte de [cheatsheets](https://github.com/Ezra-Zhao/cheatsheets) — 100 folhas de referência em um só repositório. ⭐

Una sola página para usar **PentAGI** (de VXControl): qué es, cómo se instala, cómo se lanza una prueba autorizada paso a paso, dónde mirar los resultados y la línea roja legal que no se cruza nunca.

**Autor:** Guangyi Zhao · Octubre 2026

Proyecto original: https://github.com/vxcontrol/pentagi (30.858 estrellas, consultado el 17 de octubre de 2026)

> **Nota de autoría:** esta guía es una síntesis original, redactada por el autor a partir de la documentación pública del proyecto y de su propio uso. No es una traducción ni una copia de la documentación oficial, y no es un proyecto oficial de VXControl. Para el detalle completo, ve al repositorio enlazado.
>
> **Línea roja:** PentAGI es una herramienta de pruebas de seguridad ofensivas. Úsala únicamente contra sistemas propios o con autorización escrita del propietario. Que todo corra dentro de un sandbox de Docker no te exime de la ley de tu país.

---


Apoyo y más: [GitHub Sponsors](https://github.com/sponsors/Ezra-Zhao) · [Gumroad — plantillas y cuadernos que uso](https://ezraflow28.gumroad.com) · [Ko-fi](https://ko-fi.com/ezra777zhao)

## 🇪🇸 Español

### Qué es

PentAGI es un sistema multiagente, open source y autoalojado, para pruebas de penetración autónomas. Describes el objetivo en lenguaje natural y un equipo de agentes especializados planifica el trabajo, ejecuta más de 20 herramientas profesionales (nmap, Metasploit y sqlmap entre ellas) dentro de un sandbox de Docker aislado, guarda lo aprendido en una memoria persistente (PostgreSQL con pgvector, y opcionalmente un grafo de conocimiento Neo4j/Graphiti) y te entrega el informe. Todo corre en tu infraestructura, con el modelo que tú elijas.

### Instalación

1. **Instalador interactivo + Docker Compose** en Linux, macOS o Windows: crea el directorio, descarga el instalador del repositorio y síguelo; él monta los contenedores.
2. **Configura al menos un proveedor LLM** en el `.env`. Hay más de 10: OpenAI, Anthropic, Google Gemini, AWS Bedrock, DeepSeek, GLM, Kimi, Qwen, MiniMax, Mistral y xAI, además de agregadores (OpenRouter y similares) y modelos locales con Ollama o vLLM.
3. **Entra en la interfaz web** y deja la autenticación puesta desde el primer día (también admite OAuth de GitHub/Google). Nunca la expongas a internet sin protección.

### Cómo se lanza una prueba (el flujo)

| Paso | Qué haces tú | Qué hace el sistema |
|---|---|---|
| 1. Objetivo | Describes el blanco y la meta en lenguaje natural, dentro del alcance autorizado | Crea el flujo de trabajo y el plan inicial |
| 2. Reconocimiento | Revisas el plan antes de que ejecute | Los agentes mapean hosts, puertos y servicios con las herramientas integradas |
| 3. Explotación supervisada | Apruebas o detienes pasos sensibles | Ejecuta en el sandbox, guarda cada comando y su salida en PostgreSQL |
| 4. Memoria | — | Los enfoques que funcionaron quedan guardados para flujos futuros; el grafo relaciona hosts, servicios y hallazgos |
| 5. Informe | Lees el informe (web, Markdown o PDF) y decides la remediación | Genera el informe de vulnerabilidades con guía de explotación |

Automatización: todo se puede disparar también por API REST y GraphQL con token Bearer, y la observabilidad se integra con Grafana/Prometheus.

### Qué mirar en los resultados

- **El plan y los registros paso a paso**: cada comando queda almacenado; si no puedes auditar qué hizo, no ha terminado la prueba.
- **El informe final**: vulnerabilidades encontradas con su guía de explotación, listo para priorizar arreglos.
- **La memoria**: lo aprendido alimenta la siguiente prueba; revísala antes de repetir alcance.

### ⚠️ Errores típicos

- **Apuntar a sistemas sin autorización.** Es el error que convierte una herramienta legítima en un delito. Alcance escrito primero, herramienta después.
- **Confundirlo con un simulador de ataques (BAS).** PentAGI no trae campañas ni planes de adversario predefinidos: es una plataforma de pentesting autónomo y asistido, no de emulación con guiones.
- **Modelos pequeños sin supervisión.** El propio proyecto incluye monitoreo de ejecución y planificación de tareas para que modelos abiertos rindan; activa esas opciones y revisa el plan.
- **Esperar un JSON del informe.** Las salidas documentadas son vista web, copiar, Markdown y PDF.

---

## 🇵🇹 Português

### O que é

O PentAGI é um sistema multiagente, open source e auto-hospedado, para testes de penetração autônomos. Você descreve o objetivo em linguagem natural e uma equipe de agentes especializados planeja o trabalho, executa mais de 20 ferramentas profissionais (nmap, Metasploit e sqlmap entre elas) dentro de um sandbox de Docker isolado, guarda o aprendido numa memória persistente (PostgreSQL com pgvector, e opcionalmente um grafo de conhecimento Neo4j/Graphiti) e entrega o relatório. Tudo roda na sua infraestrutura, com o modelo que você escolher.

### Instalação

1. **Instalador interativo + Docker Compose** em Linux, macOS ou Windows: crie o diretório, baixe o instalador do repositório e siga; ele sobe os contêineres.
2. **Configure pelo menos um provedor LLM** no `.env`. São mais de 10: OpenAI, Anthropic, Google Gemini, AWS Bedrock, DeepSeek, GLM, Kimi, Qwen, MiniMax, Mistral e xAI, além de agregadores (OpenRouter e similares) e modelos locais com Ollama ou vLLM.
3. **Entre na interface web** e deixe a autenticação ligada desde o primeiro dia (também aceita OAuth de GitHub/Google). Nunca exponha sem proteção à internet.

### Como se lança um teste (o fluxo)

| Passo | O que você faz | O que o sistema faz |
|---|---|---|
| 1. Objetivo | Descreve o alvo e a meta em linguagem natural, dentro do escopo autorizado | Cria o fluxo de trabalho e o plano inicial |
| 2. Reconhecimento | Revisa o plano antes de ele executar | Os agentes mapeiam hosts, portas e serviços com as ferramentas integradas |
| 3. Exploração supervisionada | Aprova ou interrompe passos sensíveis | Executa no sandbox, guarda cada comando e sua saída no PostgreSQL |
| 4. Memória | — | As abordagens que funcionaram ficam guardadas para fluxos futuros; o grafo relaciona hosts, serviços e achados |
| 5. Relatório | Lê o relatório (web, Markdown ou PDF) e decide a remediação | Gera o relatório de vulnerabilidades com guia de exploração |

Automação: tudo também pode ser disparado por API REST e GraphQL com token Bearer, e a observabilidade se integra com Grafana/Prometheus.

### O que olhar nos resultados

- **O plano e os registros passo a passo**: cada comando fica armazenado; se você não consegue auditar o que ele fez, o teste não terminou.
- **O relatório final**: vulnerabilidades encontradas com o guia de exploração, pronto para priorizar correções.
- **A memória**: o aprendido alimenta o próximo teste; revise antes de repetir o escopo.

### ⚠️ Erros típicos

- **Apontar para sistemas sem autorização.** É o erro que transforma uma ferramenta legítima em crime. Escopo por escrito primeiro, ferramenta depois.
- **Confundir com um simulador de ataques (BAS).** O PentAGI não traz campanhas nem planos de adversário predefinidos: é uma plataforma de pentesting autônomo e assistido, não de emulação com roteiros.
- **Modelos pequenos sem supervisão.** O próprio projeto inclui monitoramento de execução e planejamento de tarefas para modelos abertos renderem; ative essas opções e revise o plano.
- **Esperar um JSON do relatório.** As saídas documentadas são vista web, copiar, Markdown e PDF.

> **Linha vermelha:** o PentAGI é uma ferramenta de testes de segurança ofensivos. Use apenas contra sistemas próprios ou com autorização por escrito do proprietário. Tudo rodar dentro de um sandbox de Docker não isenta você da lei do seu país.

---

## 🇬🇧 English summary

One-page cheat sheet (Spanish + Portuguese) for **PentAGI** (VXControl): the open-source, self-hosted multi-agent system for autonomous penetration testing. You state a target and goal in plain language; specialized agents plan the work and run 20+ professional tools (nmap, Metasploit, sqlmap) inside an isolated Docker sandbox, keep persistent memory in PostgreSQL/pgvector with an optional Neo4j/Graphiti knowledge graph, and produce the report (web, Markdown or PDF). Covers the interactive Docker Compose install, the 10+ LLM providers plus local models via Ollama/vLLM, the five-step authorized-test flow, what to check in the results, and the typical mistakes — above all testing without written authorization, mistaking it for a breach-and-attack simulator, and running small models unsupervised. Original synthesis by the author from the project's public documentation; not an official VXControl document and not a translation.

**Author:** Guangyi Zhao · October 2026 · MIT License
