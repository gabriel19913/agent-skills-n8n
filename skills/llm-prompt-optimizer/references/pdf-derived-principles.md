# Princípios Derivados do Guia de Engenharia de Prompt

Resumo operacional do PDF `Guia de Engenharia de Prompt.pdf`, transformado em referência curta para esta skill.

## Fundamentos

Todo prompt forte tende a ter quatro pilares:
- `Clareza`: tarefa específica, sem verbos vagos nem múltiplas interpretações.
- `Contexto`: cenário, objetivo, público, nível de profundidade e restrições relevantes.
- `Formato`: como a resposta deve vir.
- `Restrições`: o que evitar, limitar ou priorizar.

Estrutura base recorrente:

```markdown
CONTEXTO + TAREFA + FORMATO + RESTRIÇÕES
```

## Técnicas intermediárias

### Role prompting
Use quando a resposta precisa de expertise, perspectiva ou tom específico.

### Few-shot prompting
Use quando exemplos curtos ajudam mais do que descrição abstrata.

### Output structuring
Defina schema, headings, listas, tabelas ou JSON quando a forma de saída importa.

### Análise passo a passo
Útil para lógica, comparação, debugging, priorização e tomada de decisão.

## Técnicas avançadas

### Mega prompt
Ideal para agentes, automações, assistentes especializados e casos de uso recorrentes.

### Iteração
Refine por partes: tom, estrutura, conteúdo ou formato, sem recomeçar do zero toda vez.

### Self-reflection
Peça uma revisão final de clareza, completude, precisão e aderência ao formato.

### Prompt chaining
Quebre tarefas grandes em etapas menores quando uma única instrução produziria uma resposta superficial ou caótica.

## Critério de qualidade

Um prompt bom é:
- específico sem ser engessado;
- completo sem ser prolixo;
- adaptado ao objetivo real;
- explícito sobre formato e restrições;
- consistente com a complexidade da tarefa.

## Checklist rápido

Antes de considerar um prompt pronto, verifique:
- o contexto necessário foi dado;
- a tarefa está inequívoca;
- o formato de saída está definido;
- há exemplos quando o padrão precisa ser replicado;
- as restrições evitam respostas ruins comuns;
- o prompt não ficou longo só por parecer sofisticado.
