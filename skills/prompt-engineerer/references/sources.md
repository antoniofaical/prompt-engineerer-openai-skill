# Fontes e decisões de adaptação

## Proveniência

Base: [antoniofaical/prompt_engineerer](https://github.com/antoniofaical/prompt_engineerer/tree/4d7d3dc9050c4f65d76bc216d6978392f495658b), commit `4d7d3dc9050c4f65d76bc216d6978392f495658b`. A adaptação usa `resources/system.md`, `resources/guidelines.json`, `resources/sources.md`, `resources/evaluation-cases.json` e o comportamento de `pipeline.py` e `config.py`.

O projeto registra revisão do catálogo em 2026-09-25. A conversão foi feita em 2026-10-13. As consultas do projeto original são históricas: esta adaptação não afirma ter revalidado todas as fontes nem suas alegações científicas.

## Rastreabilidade das regras

| ID | Fonte | Tratamento nesta adaptação |
|---|---|---|
| `openai-guide` | [Prompt engineering](https://developers.openai.com/api/docs/guides/prompt-engineering) | Página oficial consultada em 2026-10-13; clareza, separação de mensagens e delimitação. Nenhum modelo gerador foi fixado. |
| `openai-reasoning` | [Reasoning best practices](https://developers.openai.com/api/docs/guides/reasoning-best-practices) | Página oficial consultada em 2026-10-13; objetivos diretos e ausência de exigência de cadeia de pensamento. |
| `anthropic-best-practices` | [Claude prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) | Curadoria herdada do projeto; exemplos e delimitação condicionais. Não reconsultada nesta conversão. |
| `anthropic-overview` | [Prompt engineering overview](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/overview) | Curadoria herdada; critérios e avaliação proporcionais. Não reconsultada. |
| `anthropic-context-engineering` | [Effective context engineering](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) | Curadoria herdada; seleção de contexto relevante. Não reconsultada. |
| `claude-blog-2026` | [Best practices for prompt engineering](https://claude.com/blog/best-practices-for-prompt-engineering) | Curadoria herdada; honestidade sobre lacunas como orientação, sem garantia. Não reconsultada. |
| `white-pattern-catalog` | [A Prompt Pattern Catalog](https://arxiv.org/html/2302.11382v1) | Curadoria herdada; esclarecimento e perspectiva profissional condicionais. Não importar o catálogo inteiro. |
| `re-systematic-review` | [Revisão sobre engenharia de requisitos](https://arxiv.org/abs/2507.03405) | Curadoria herdada, limitada ao domínio de requisitos. O projeto original consultou o resumo; detalhes numéricos não foram incorporados. |
| `project-design` | `system.md`, `pipeline.py` e README do projeto original | Decisões de produto para preservar intenção, capacidades, contexto e arquivos; não são resultados científicos. |

## Formato da skill

[Build skills](https://learn.chatgpt.com/docs/build-skills), documentação oficial consultada em 2026-10-13: diretório com `SKILL.md`, metadados de nome e descrição, recursos opcionais e leitura progressiva. `agents/openai.yaml` identifica a skill na interface e mantém seleção implícita habilitada. A skill não declara dependência de MCP ou API.

## Decisões de conversão

- O agente da conversa substitui o gerador via API; removidos bootstrap, credenciais, SDK, retries e configuração obrigatória em TOML.
- As etapas de autoria continuam presentes, sem envelopes JSON ou schemas internos obrigatórios.
- Defaults de chat e idioma automático são preservados. Limites de perguntas e correções são orientações proporcionais, não uma reprodução do loop da CLI.
- Saída na conversa é padrão. Gravação em arquivo exige pedido; o seed é preservado, e falha impeditiva não substitui resultado anterior.
- As verificações antes realizadas em Python passam a ser instruções comportamentais. Esta skill não oferece a mesma garantia determinística de IDs, validação de configuração, lock e gravação da aplicação original.
- O índice original de fontes não é uma base operacional adicional: suas generalizações já foram corrigidas no catálogo. Não há quantidade obrigatória de exemplos, ganho percentual garantido, XML obrigatório, exigência de persona ou cadeia de pensamento privada.
- Não se afirma implementar DSPy, PDR, GEPA, MIPROv2 ou otimização empírica. Essas referências não originam regras nesta versão.

## Manutenção

Ao mudar uma recomendação, confira a fonte primária pertinente, registre data e limites e repita os casos afetados de [evaluation-cases.md](evaluation-cases.md). Quando a fonte não sustentar uma orientação específica, use orientação geral ou remova a afirmação. Não confunda existência de um nome de modelo, acesso à conta e disponibilidade de ferramentas.
