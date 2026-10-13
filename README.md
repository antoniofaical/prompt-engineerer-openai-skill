# Prompt Engineerer — OpenAI Skill

Skill em português para transformar demandas e prompts existentes em prompts claros, autocontidos e revisados para outra IA. Adapta o método de [prompt_engineerer](https://github.com/antoniofaical/prompt_engineerer/tree/4d7d3dc9050c4f65d76bc216d6978392f495658b) ao agente da conversa, sem programa Python, chave de API ou modelo gerador fixo.

O fluxo interpreta a demanda, esclarece ambiguidades materiais, escolhe técnicas pertinentes, escreve e revisa o prompt. Preserva restrições e contexto, distingue ferramentas ausentes de desconhecidas e trata contradições antes de finalizar.

## Instalação e uso

No Codex, peça ao instalador:

```text
Use $skill-installer para instalar a skill de
https://github.com/antoniofaical/prompt-engineerer-openai-skill/tree/main/skills/prompt-engineerer
```

O instalador escolhe o diretório adequado ao ambiente. Para instalação manual, copie a pasta inteira `skills/prompt-engineerer` para um diretório de skills reconhecido pela sua versão. A [documentação oficial](https://learn.chatgpt.com/docs/build-skills) descreve os locais de descoberta e a instalação por repositório. Se a skill não aparecer, reinicie o aplicativo.

Exemplo de invocação:

```text
Use $prompt-engineerer para transformar esta demanda em um prompt:
quero comparar três soluções de gestão de estoque para clínicas com base
nas descrições e preços que vou fornecer. Preciso de uma tabela e uma
recomendação justificada, sem inventar funcionalidades.
```

Também é possível pedir a melhoria de um prompt existente ou indicar um arquivo para autoria. Informe quando relevante o modelo destinatário, ferramentas disponíveis, finalidade (`chat`, `api_user` ou `api_system`) e idioma do prompt. O idioma da resposta desejada pode ser diferente. Nada disso exige formulário ou TOML.

A seleção automática fica habilitada para pedidos de criar, melhorar, adaptar ou revisar prompts. A skill escreve o prompt; um pedido direto de redigir um email ou analisar um artigo deve continuar sendo atendido como tarefa direta, sem ativar esta skill automaticamente.

## Conteúdo

```text
skills/prompt-engineerer/
├── SKILL.md
├── agents/openai.yaml
└── references/
    ├── guidelines.md
    ├── sources.md
    └── evaluation-cases.md
```

- [SKILL.md](skills/prompt-engineerer/SKILL.md): contrato de autoria e fluxo.
- [Guidelines](skills/prompt-engineerer/references/guidelines.md): regras centrais e técnicas condicionais, com rastreabilidade das 16 regras do catálogo original.
- [Fontes](skills/prompt-engineerer/references/sources.md): proveniência, datas e limites da conversão.
- [Avaliação](skills/prompt-engineerer/references/evaluation-cases.md): casos de autoria, revisão, conflitos e seleção da skill.
- [Registro da verificação inicial](evals/2026-10-13.md): saídas produzidas e revisão manual, com limitações explícitas.

## Limites e avaliação

O resultado padrão é um prompt pronto para copiar; gravação em arquivo ocorre quando solicitada. A skill não executa a tarefa descrita no seed nem habilita ferramentas na IA destinatária.

As instruções substituem parte das verificações determinísticas do programa original. Revisão textual e validação do formato da skill não comprovam ganho de qualidade na resposta da destinatária. Para avaliar esse ganho, compare respostas ao seed e ao prompt gerado no mesmo modelo, em conversas separadas, usando os critérios dos casos. Registre modelo, data e configurações; quando possível, use avaliação cega.

Não há integração adicional com API nem scripts de execução nesta versão. As fontes históricas são identificadas como herdadas; não há promessa de compatibilidade com todos os modelos ou de prompt universalmente ótimo.
