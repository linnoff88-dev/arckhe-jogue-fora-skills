# Jogue fora os seus skills

![Jogue fora os seus skills](docs/capa.jpg)

Dicas, prompt e script para fazer a faxina das skills do seu agente (Claude Code, Codex e cia.) e ficar sÃ³ com as que ainda ganham a vaga.

> Em 22/10/2026 a Anthropic doou o padrÃ£o **Agent Skills** para o Agentic AI Foundation, da **Linux Foundation** (a mesma casa do MCP). O formato fica. Mas os modelos de hoje precisam de cada vez menos "cola": skill demais polui o contexto e aumenta a chance de o modelo escolher a errada.

## O que tem aqui

| arquivo | o quÃª |
|---|---|
| [`COMECE-AQUI.md`](COMECE-AQUI.md) | como rodar a auditoria em 4 passos |
| [`PROMPT-AUDITORIA.txt`](PROMPT-AUDITORIA.txt) | o prompt em portuguÃªs, pronto para colar (sÃ³ leitura, gera um relatÃ³rio HTML) |
| [`TRES-PERGUNTAS.md`](TRES-PERGUNTAS.md) | as trÃªs perguntas para cada skill + a dica "skill na hora certa" |
| [`scripts/auditar_skills.py`](scripts/auditar_skills.py) | contagem local, sem IA e sem internet: quantas skills, quais vocÃª usa, peso das descriÃ§Ãµes |

## 10 dicas rÃ¡pidas

1. **Cada skill instalada deixa nome e descriÃ§Ã£o em toda sessÃ£o.** Uma pesa pouco; cem juntas poluem o contexto.
2. **Cem skills sÃ£o cem chances de escolher a errada.** Seis skills de design parecidas deixam o resultado sorteado, nÃ£o melhor.
3. **Skill era muleta de modelo fraco.** Em 2025 o modelo precisava do passo a passo; os de hoje deduzem os prÃ³ximos passos sozinhos.
4. **Muita skill cabe numa linha.** Ex.: em vez de uma skill de 300+ palavras que faz a IA te interrogar, uma linha no `AGENTS.md`: *"quando o pedido nÃ£o estiver claro, me faÃ§a perguntas antes de comeÃ§ar."*
5. **Fica a skill que roda cÃ³digo exato** (o mesmo tratamento toda vez).
6. **Fica a skill que sabe o que o modelo nÃ£o sabe** (seu processo, seus clientes, seu estilo) â€” desde que nÃ£o repita o `memory.md`.
7. **Sai a skill que um conector/MCP oficial jÃ¡ resolve.** Confira antes se ele cobre a tarefa.
8. **Duas skills que se sobrepÃµem viram uma**, mais enxuta, com o melhor de cada.
9. **Nunca apague direto:** mova para uma pasta de backup com data.
10. **Skill rara entra na hora certa:** guarde numa pasta que o agente nÃ£o carrega sozinho e peÃ§a "lÃª a skill X e segue" quando precisar.

## Prova real (mÃ¡quina do INEMA, 24/10/2026)

Rodando `scripts/auditar_skills.py --dias 90 --projetos ~/projetos`:

- **328** skills encontradas, **78** sÃ³ de plugins;
- **129** com uso registrado nos Ãºltimos 90 dias, **199** sem uso observado;
- as **10** mais usadas somam **47%** de todos os usos;
- **~16,5 mil** palavras de descriÃ§Ã£o somadas no inventÃ¡rio.

![RelatÃ³rio da auditoria](docs/relatorio-exemplo.png)

(Contagem local do histÃ³rico do Claude Code e do Codex; histÃ³rico ausente = uso desconhecido.)

## O processo, do inÃ­cio ao fim

| # | passo | comando | quem |
|---|---|---|---|
| 1 | Contar as skills e o uso (rÃ¡pido, local) | `python3 scripts/auditar_skills.py --dias 90 --projetos ~/projetos --json auditoria.json` | âš™ï¸ script |
| 2 | Auditoria completa com relatÃ³rio HTML | colar `PROMPT-AUDITORIA.txt` numa sessÃ£o nova do Claude Code/Codex | ðŸ§  vocÃª + agente |
| 3 | Ler o relatÃ³rio e decidir (Manter/Juntar/Arquivar/Revisar) | abrir `auditoria-skills-AAAA-MM-DD/relatorio.html` | ðŸ§  vocÃª |
| 4 | Pedir a limpeza das skills escolhidas, com backup com data | "move as skills X, Y, Z para ~/skills-backup-AAAA-MM-DD" | ðŸ§  vocÃª + agente |
| 5 | Guardar as de uso raro fora da pasta carregada | mover para `~/skills-guardadas/` e chamar "lÃª a skill X e segue" | ðŸ§  vocÃª |
| 6 | Repetir a cada trimestre | voltar ao passo 1 | âš™ï¸ / ðŸ§  |

## VÃ­deo

VÃ­deo explicativo (16:9 e 9:16): links em [`VIDEOS.md`](VIDEOS.md).

---

Projetos e cursos abertos e gratuitos: **https://inema.club**

---

Projeto adaptado da comunidade INEMA TDS - Marca Arckhe