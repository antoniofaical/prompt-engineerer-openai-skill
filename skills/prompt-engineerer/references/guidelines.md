# Catálogo de guidelines

Adaptação do catálogo operacional `guidelines.json` v1.0.0 do projeto original, revisto nele em 2026-09-25. Use as condições e exceções para escolher somente as técnicas úteis. Os IDs permitem manutenção e rastreabilidade; não pertencem ao prompt final. Veja [sources.md](sources.md) apenas para investigar uma fonte ou atualizar uma regra.

## Regras centrais

| ID | Orientação | Exceção ou limite | Fonte |
|---|---|---|---|
| `preserve_intent` | Preserve objetivo, fatos e restrições; não acrescente exigências sem apoio no pedido. | Sugestões não viram requisitos silenciosamente. | `project-design` |
| `clear_deliverable` | Declare ação e entrega esperada em linguagem direta. | Não imponha formato que contrarie o usuário. | `openai-guide` |
| `honest_gaps` | Diferencie informações fornecidas de lacunas. | Ficção é permitida quando solicitada e identificada. | `claude-blog-2026` |
| `capabilities` | Atribua apenas capacidades declaradas. Para capacidades desconhecidas, use condição ou alternativa realizável. | Provedor e modelo não comprovam acesso a ferramentas; lista vazia não admite presumir ferramentas. | `project-design` |

## Técnicas gerais condicionais

| ID | Quando usar | Orientação e limite | Fonte |
|---|---|---|---|
| `relevant_context` | Documentos ou contexto extenso. | Delimite instruções, dados e exemplos; remova redundância sem truncar fatos essenciais nem remeter apenas ao seed invisível. | `anthropic-context-engineering` |
| `examples` | Formato ou critérios difíceis de descrever. | Use exemplos pertinentes quando disponíveis, sem quantidade fixa. Não atribua exemplos inventados ao usuário; identifique hipóteses. | `anthropic-best-practices` |
| `purpose` | A finalidade de uma restrição melhora sua interpretação. | Explique-a brevemente; omita motivos redundantes ou especulativos. | `anthropic-best-practices` |
| `checkable_quality` | A entrega precisa ser verificável. | Expresse os critérios de sucesso fornecidos e uma forma proporcional de verificá-los; não imponha avaliação extensa a uma tarefa simples. | `anthropic-overview` |
| `clarify_material` | Ambiguidade que muda a entrega. | Pergunte de forma direcionada ou indique a entrada necessária à destinatária. Não repita respostas nem bloqueie por escolhas menores. | `white-pattern-catalog` |
| `task_steps` | Partes complexas com dependências. | Organize etapas verificáveis dentro do fluxo disponível; não exija infraestrutura de agentes ou chamadas adicionais inexistentes. | `project-design` |
| `evidence` | Pesquisa, comparação factual ou análise documental. | Peça evidências e distinção entre fatos, inferências e incertezas, respeitando acesso a fontes. Não peça referências fabricadas nem alegue navegação sem ferramenta. | `project-design` |
| `role_perspective` | Perspectiva profissional muda os critérios da tarefa. | Defina responsabilidades concretas; não invente credenciais, experiência pessoal ou persona ornamental. | `white-pattern-catalog` |
| `requirements_phase` | Engenharia de requisitos. | Adapte perguntas e validação à fase informada. Não generalize o domínio a todas as demandas; revisão por IA não prova validade dos requisitos. | `re-systematic-review` |

## Técnicas condicionais por provedor

Use somente quando o destino correspondente estiver identificado. Elas não comprovam compatibilidade de um modelo ou endpoint específico. Outros destinos e modelos desconhecidos recebem as orientações gerais.

| ID | Destino e condição | Orientação e limite | Fonte |
|---|---|---|---|
| `claude_delimiters` | Anthropic; mistura de instruções, documentos e exemplos. | Considere tags descritivas ou cabeçalhos consistentes. XML é opcional; Markdown simples pode bastar. | `anthropic-best-practices` |
| `openai_role` | OpenAI; finalidade de API. | Separe instruções duradouras de entradas da execução. O texto não altera a hierarquia; a aplicação deve mapear o papel suportado, inclusive `developer` quando aplicável. | `openai-guide` |
| `reasoning_evidence` | OpenAI; resolução de problemas. | Peça objetivos claros, resposta justificada e verificação objetiva, sem roteiro de raciocínio privado. Cálculos e demonstrações verificáveis continuam apropriados. | `openai-reasoning` |

Não transforme XML, personas, número de exemplos, etapas ou tamanho do prompt em requisitos universais. Preserve também as proibições explícitas do usuário; a preferência por instruções positivas não as elimina.
