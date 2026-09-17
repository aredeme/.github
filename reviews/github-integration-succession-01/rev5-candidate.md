# Review object — PADRÃO rev5 candidate

> Review-only artifact for `aredeme/.github#38`. This file is **not** the canonical norm and must not be merged as authority. The canonical `PADRÃO — Ciclo Issue → Pull Request → Release`, UUID `97421b14-1a2d-411e-a142-5b49e85efb03`, remains rev4 VIGENTE in Arede Docs until separately promoted.

**Base:** rev4 VIGENTE, 10/09/2026  
**Candidate status:** `PREPARED_FOR_INDEPENDENT_REVIEW`  
**Purpose:** remove the normative dependency on the proprietary `arede-github-projects` MCP/runtime without weakening governance guarantees.

This is an exact semantic delta: every rev4 section not replaced below remains unchanged for the future rev5.

## §9 — Status — nominal replacement

Replace the sentence that assigns structural-suspicion signaling specifically to the MCP with:

> `Initiative`/`Feature` são containers de outcome. Em uso normal, não precisam de `Ready` nem `In review`; esses estados pertencem principalmente às work units. O mecanismo de coordenação/enforcement aplicável sinaliza combinação estrutural suspeita em vez de inventar transição.

## §13 — Admission plan obrigatório — replace fully

**Nenhuma admissão nova ao Project principal ocorre fora do caminho governado**, ainda que exista primitive raw tecnicamente acessível por API, MCP, UI, Action, CLI ou outra ferramenta.

**Nenhuma remoção, arquivamento ou evicção de item central ocorre fora do caminho governado**, ainda que exista primitive raw tecnicamente acessível. A saída da fila preserva a Issue e seus vínculos, usa decisão fresca e reversível quando a plataforma permitir, declara a pós-condição esperada, verifica-a na fonte proprietária conforme §14 antes de considerar a saída concluída, e falha fechado diante de qualquer resultado que não seja sucesso confirmado.

Antes de qualquer add ou saída, a coordenação resolve e avalia, no mínimo:

- a Issue exata e seu estado atual;
- `Type`, `Parent`, Issue Fields e vínculos relevantes;
- presença ou ausência do item no Project;
- profundidade, ciclo e coerência de hierarchy;
- função operacional central;
- possível duplicidade material quando houver evidência suficiente;
- decisão `ADMIT`, `EVICT`, `REPO_ONLY`, `RECONCILE` ou `STOP`;
- schema/migration stage observado e freshness material usada na decisão.

Essa decisão pode ser produzida pelo sistema de coordenação, por policy executável, por automação governada ou por outro mecanismo admitido. **Não existe obrigação de banco de plans, runtime próprio ou serviço intermediário** quando a decisão puder ser provada e aplicada com segurança sem eles.

`EVICT` aplica-se somente a item já presente cuja saída central esteja materialmente justificada. A decisão deve identificar alvo exato, motivo, estado observado, preservação de histórico/vínculos, operação reversível quando disponível e pós-condição esperada.

Broad auto-add por simples condição de `open`, repositório, label ou filtro genérico permanece proibido como mecanismo principal. Auto-add futuro só pode consumir sinal governado equivalente à decisão acima.

Uma primitive raw de add/archive/remove/update é apenas **mecanismo de aplicação**. A existência de acesso técnico à primitive não cria authority e não permite contornar policy, hierarchy, freshness ou Gate aplicável.

Toda decisão que resulte em `ADMIT` ou `EVICT` central deixa registro recuperável na própria Issue afetada ou em objeto já vinculado a ela, com alvo exato, decisão, migration stage observado e freshness usada — é isso que torna o ato governado distinguível de add/remoção raw por conveniência. As demais decisões são registradas de forma recuperável somente quando isso for material para continuidade, disputa, risco, auditoria ou prevenção de retrabalho; `REPO_ONLY`/`STOP` rotineiros não exigem log permanente por ritual. Nenhum banco de plans, journal, serviço ou runtime próprio é exigido para isso: a superfície proprietária do próprio objeto já é suficiente.

Resultado ambíguo falha fechado.

## §14 — Enforcement independente de transporte — replace fully

A governança do Project é propriedade do **sistema de coordenação/policies da Arede**, não de um protocolo, fornecedor, cliente ou conector específico.

A execução pode usar, conforme capability e necessidade real:

- API oficial do GitHub;
- GitHub MCP oficial ou outra integração oficial disponível;
- GitHub Actions;
- UI/CLI quando o ato for humano ou operacionalmente apropriado;
- outra superfície admitida que preserve as mesmas invariantes.

Nenhuma dessas superfícies vira fonte de authority por existir.

O enforcement material deve garantir, quando aplicável:

- alvo/Project/Issue exatos;
- authority/capability suficiente;
- schema/migration stage compatível com o efeito;
- hierarchy/admission/transição válidas;
- freshness suficiente imediatamente antes da mutation quando a decisão depender de estado previamente lido;
- pós-condição declarada antes do efeito e verificada na fonte proprietária antes de reportar sucesso, quando a mutation for material;
- retry de mutation somente nas condições de §17; nenhum rótulo de resultado autoriza repetição por si.

Sucesso não se presume a partir da resposta da superfície. Para mutation material — admissão, saída da fila, `Type`/`Parent`/hierarchy, `Status`, Gate ou schema — o resultado só é sucesso depois que releitura suficiente da fonte proprietária confirmar a pós-condição declarada. Qualquer outro resultado é classificado pelo que a fonte proprietária prova sobre o efeito, nunca pela resposta da superfície: `FAILED` somente quando a releitura provar conclusivamente que nenhum efeito ocorreu; **reconciliação necessária** quando houver efeito parcial, divergente ou diferente do declarado, ainda que a superfície tenha reportado êxito; `UNKNOWN` quando a releitura for impossível ou inconclusiva, ou a pós-condição ainda não for observável. Erro explícito da superfície é apenas sinal: não prova ausência de efeito e, sem releitura conclusiva, é `UNKNOWN`. Nenhum desses rótulos autoriza repetição por si; retry segue exclusivamente §17. A exigência é proporcional: operação trivial, sem efeito governado e sem prova dependente, não exige releitura por ritual.

Não existe requisito de `arede-github-projects`, GitHub Gateway próprio, MCP próprio, contrato de runtime próprio, banco de plans ou proxy intermediário por antecipação.

Componente próprio só nasce quando uma lacuna concreta das superfícies disponíveis passar pelo H7/H8 do `00 — Contrato da Fundação Arede v1` e possuir consumidor real que justifique lifecycle próprio.

## §15 — Schema, estágios e fail-closed — replace fully

Antes de mutation governada, a coordenação deve observar o **schema vivo no estágio atual** suficiente ao efeito solicitado.

O contrato deve distinguir, quando material, estágio legado, etapas intermediárias de migração e estágio-alvo. Assim, ausência de `Risk`/`Area` **não é tratada como drift antes do cutover** se o estágio corrente ainda governa `Risco`/`Módulo`; após o cutover, o inverso passa a ser validado.

Cada estágio possui expectativas explícitas e monotônicas suficientes para evitar janela em que duas representações disputem propriedade.

Condições que impedem write incluem, quando materiais:

- fonte normativa/authority necessária divergente, stale ou indisponível;
- migration stage desconhecido ou incompatível;
- field obrigatório naquele estágio ausente ou ambíguo;
- option incompatível/ausente;
- owner/origem do field diferente do contrato vigente;
- Type/Parent/hierarquia inválidos;
- decisão calculada sobre estado que avançou materialmente;
- Project/Issue diferentes do alvo aprovado;
- resultado anterior de mutation ainda `UNKNOWN` ou em reconciliação necessária, quando ele puder interferir no novo efeito;
- duplicidade material não resolvida;
- authority/capability insuficiente.

Não conformidade estrutural **preexistente** de item legado não bloqueia, por si só, transição operacional que não crie nem agrave essa não conformidade. O diagnóstico registra o drift para reconciliação planejada. O fail-closed por `Type`/`Parent`/hierarquia aplica-se integralmente a nova admissão e a mutation que crie ou agrave estrutura inválida. Se a operação solicitada depender materialmente da estrutura ainda não reconciliada e não for possível determinar sua segurança, retorna `STOP`.

Schema drift não é corrigido silenciosamente pelo caminho cotidiano de mutation. Mudança estrutural usa migração própria, revisável e reconciliada.

Nenhum `contract version` executável separado é obrigatório quando a própria norma vigente + estado vivo + capability da ferramenta forem suficientes para provar a decisão. Se código executável próprio codificar regras materiais, sua versão/objeto deve ser vinculável à norma que implementa e não ganha authority por estar rodando.

## §16 — Identidade da execução quando material — replace fully

A identidade da ferramenta/runtime que executa uma operação só precisa ser materializada quando ela mudar segurança, capability, semântica da mutation, auditabilidade ou possibilidade de provar o objeto executado.

Quando material, a evidência suficiente pode incluir, conforme a superfície:

```text
caller/principal
capability/permission relevante
provider/surface
source SHA ou workflow/version quando houver código próprio
norma/authority consumida
API/version/contract do provider quando diferença de comportamento for material
```

Não existe obrigação de criar um runtime intermediário apenas para produzir essa identidade.

Versão declarada sem vínculo ao objeto realmente executado não basta quando o fingerprint é material. Da mesma forma, nome de ferramenta, login ou protocolo não substituem authority/capability.

Drift material observado entre source, norma vigente e objeto realmente executado, ou entre a capability/semântica esperada da superfície e a observada, bloqueia até reconciliação o efeito que dependa da propriedade divergente.

## §17 — Retry e reconciliação — keep rule, adjust wording

Read pode repetir quando o contrato garantir segurança.

Mutation cujo resultado não seja sucesso confirmado nunca recebe retry cego, qualquer que seja o sinal da superfície ou o rótulo atribuído conforme §14 — timeout, erro explícito, `UNKNOWN`, reconciliação necessária ou mesmo `FAILED`. Primeiro reler a fonte proprietária e reconciliar o efeito real. Repetir somente quando a fonte proprietária provar ausência do efeito (`FAILED` conforme §14) ou quando idempotência ou outra condição observada no alvo excluir efeito duplicado; releitura inconclusiva não é comprovação e falha fechado. Efeito parcial ou divergente não é repetido: é reconciliado, e só então se decide nova mutation. Toda repetição é nova mutation e passa integralmente pelas pré-condições de §14 e §15 — `FAILED` satisfaz a prova de ausência de efeito, mas não substitui authority, freshness e alvo revalidados.

Operação composta que pare após mutation parcial retorna estado explícito de reconciliação necessária; não mascara sucesso nem continua por presunção.

Essa regra pertence ao método Arede e se aplica independentemente de a mutation ter sido executada por API, MCP, Action, UI, CLI, serviço próprio ou outra superfície.

## §28 — Migração e compatibilidade — replace items 2, 6, 7 and closing paragraphs

Keep the rev4 caput and unchanged items. The Project-migration prerequisites become:

1. esta revisão estar promovida pela authority aplicável;
2. a superfície de coordenação/enforcement escolhida estar disponível e já ter sido provada em fluxo representativo e revisável — leitura → decisão governada → mutation autorizada → releitura da pós-condição —, com caso negativo que termina sem mutation, consumindo a norma vigente e o migration stage aplicável, sem exigir runtime próprio quando as superfícies oficiais forem suficientes;
3. existir diagnóstico read-only do drift atual;
4. existir plano exato e reversível para **schema, Organization Issue Fields, Project fields, views e hierarchy/parents dos itens existentes**;
5. a reconciliação de propriedade em `POLÍTICA — Fontes de verdade` estar preparada para o cutover `Módulo/Risco -> Area/Risk`;
6. o caminho de mutation admitido impedir que nova admissão desorganizada recrie o problema durante a limpeza;
7. cada mutation resolver/revalidar o objeto vivo, falhar fechado se o estágio tiver avançado materialmente e ter a pós-condição verificada conforme §14 antes de o lote ser dado por concluído; item cuja pós-condição não se confirme é classificado conforme §14 e só é repetido nas condições de §17.

Closing paragraphs:

> A promoção desta norma não autoriza, por consequência, restaurar, manter, remover ou criar conector/runtime GitHub próprio. A escolha da superfície de integração é substituível e deve seguir consumidor real, capacidade nativa disponível, custo total, authority e H7/H8.
>
> Aposentadoria de predecessor técnico exige substituição real provada, não prova documental. São condições cumulativas: a superfície sucessora estar operante no caminho real sob authority aplicável; as capacidades que continuam materialmente necessárias estarem provadas nessa superfície; os consumidores materiais estarem identificados e efetivamente migrados ou cortados para ela; nenhum consumidor material, humano ou automatizado, ainda depender do predecessor; e o cutover estar provado por pós-condição observada. Enquanto qualquer uma dessas condições não estiver provada, a aposentadoria falha fechado e o predecessor permanece.
>
> Capacidade do predecessor sem consumidor material real não exige paridade: é classificada como dispensada conforme H3/H7, não como pendência de prova. Cada objeto do predecessor — repositório, runtime, workflow, IaC, App ou credencial — é aposentado sob a authority e o boundary que lhe são próprios; a prova relativa a um objeto não autoriza a retirada de outro.

## §29 — Efeito desta revisão — replace fully

A revisão 5 preserva integralmente as decisões de Project/hierarchy/schema/lifecycle da revisão 4, exceto pelo acoplamento do enforcement a um MCP próprio.

Em especial, a revisão 5:

- mantém o Project central como fila transversal seletiva e preserva a recuperabilidade de Issues repo-locais;
- mantém hierarchy nativa, migration stages, `Risk`/`Area` prospectivos, `Status`, `Executor`, Gate, Ready/Done e as views-alvo definidos na rev4;
- mantém broad auto-add proibido e mantém add/remoção/arquivamento/evicção sujeitos a decisão governada, fresca e recuperável no próprio alvo quando resultarem em `ADMIT`/`EVICT`;
- preserva fail-closed, authority/capability, freshness material, pós-condição verificada em mutation material e reconciliação antes de retry para qualquer resultado que não seja sucesso confirmado;
- condiciona a aposentadoria de predecessor técnico a substituição operante no caminho real, cutover provado dos consumidores materiais e ausência de consumidor remanescente, sem exigir paridade com capacidade sem consumidor real;
- estabelece que policy/enforcement pertencem ao sistema Arede e **não** ao protocolo ou conector usado para alcançar o GitHub;
- permite usar superfícies oficiais/API/MCP/Actions/UI/CLI adequadas sem criar proxy próprio por ritual;
- elimina a obrigação de `arede-github-projects`, GitHub Gateway próprio, runtime MCP dedicado, identidade específica de connector ou banco de plans;
- mantém código próprio possível somente diante de lacuna comprovada com consumidor real, conforme H7/H8;
- não autoriza por consequência migration do Project, remoção do predecessor, alteração de workflow, revogação de App/credencial, mudança de infraestrutura ou qualquer efeito live.

## Promotion-time nominal sweep

When materializing rev5 into the canonical document, the sweep is a **nominal substitution only**: it applies solely the replacements in this delta and may not remove, weaken or reassign any obligation, fail-closed condition, postcondition, freshness requirement or authority attribution in any section. Any other rev4 section still treating `MCP`, `arede-github-projects`, `runtime MCP`, `connector version` or equivalent language as an **architectural requirement** is listed and becomes an explicit delta, reviewed before promotion — not rewritten at materialization time. Historical/provenance references may remain when clearly qualified as predecessor.

## Independent-review questions

Review only these material questions:

1. Was any material guarantee of rev4 weakened by decoupling from the MCP?
2. Does the candidate introduce any new service/framework obligation that violates H7/H8?
3. Do `UNKNOWN`, freshness, authority, hierarchy, and migration stage remain fail-closed where material?
4. Does the text create dual authority or permit raw writes without policy?
5. Is the delta sufficient to allow `arede-github-projects` to be retired **later**, without prematurely authorizing retirement before substitution is proved?

**Expected review output:** findings classified P0/P1/P2/P3, with exact section references. P0/P1/P2 are material; P3 is advisory. Do not modify files or implement changes. The canonical norm remains rev4 VIGENTE.
