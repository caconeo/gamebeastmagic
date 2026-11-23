# GAME BEAST MAGIC — WAR OF REALMS

## Dossiê consolidado de desenvolvimento · 23 de novembro de 2026

**Estado da entrega.** Há um RPG de ação 3D executável localmente no Chrome. O jogador controla o Celestial Archmage, explora a Floresta Arcana, enfrenta o Guardião e dá ordens a um aliado. A galeria permite comparar 35 modelos animados com suas cartas. A Trilha do Santuário é uma segunda cena de avaliação visual. Os quatro mundos, a campanha de até 200 fases e o multiplayer continuam no planejamento.

### Como experimentar

Na pasta `desenvolvimento-v2`, com as dependências instaladas, execute `npm run dev -- --host 127.0.0.1 --port 5174 --strictPort` se o servidor local estiver desligado.

| Experiência | O que observar |
|---|---|
| [Floresta com o Spirit Wolf](http://127.0.0.1:5174/?aliado=spirit_wolf&qualidade=alto) | WASD move o protagonista. Shift corre, Espaço salta, C esquiva. No pátio, E desafia o Guardião, J golpeia e K lança o cometa. O seletor de ordens controla o aliado. |
| [Trilha do Santuário](http://127.0.0.1:5174/?scene=trilha&qualidade=alto) | Caminhe até a ponte e atravesse o arco para avaliar escala, relevo, câmera e leitura do personagem em movimento. |
| [Galeria](http://127.0.0.1:5174/?scene=elenco) | Selecione o personagem e o clipe. Arraste para girar e use a roda para aproximar o modelo da distância de inspeção. |

### Da auditoria à versão jogável

| Entrega | Resultado e evidência |
|---|---|
| Auditoria e V2-00 | O ZIP original contém o jogo de tabuleiro React/Phaser. Cartas, IDs, facções e lore servem de referência ao RPG. Nacre forneceu referências técnicas e o Observatório v03, referências de combate e rede. Foram inventariados 421 arquivos por SHA-256 e preservadas 39 entradas em ZIP recuperável. [Auditoria](Auditoria_Tecnica_Antigravity.md) |
| V2-01 · Fundação | Projeto independente em TypeScript 5.9.3, Babylon.js 8.0.0 e Vite 7.3.1. Cena WebGL com carregamento, redimensionamento, tratamento de erro, build e testes locais. [Registro V2-00/01](../desenvolvimento-v2/docs/V2-00_V2-01.md) |
| V2-02 · Controle | Movimento relativo à câmera, aceleração, frenagem, corrida, salto, gravidade, esquiva e colisões. Câmera suavizada com órbita, zoom e correção de oclusão. Os sete critérios receberam aprovação manual do responsável pelo projeto. [Controlador](../desenvolvimento-v2/docs/V2-02.md) |
| V2-03 · Archmage | Inspeção do kit, cópia de trabalho, rig humanoide, encaixes de mão, cajado e cristais, seis clipes de locomoção e mistura de poses. Barba e manto acompanham ossos auxiliares. [Rig e animação](../desenvolvimento-v2/docs/V2-03.md) |
| V2-04 · Floresta | Ruínas, portal, trilha, árvores, cristais, luz, névoa, sombras e perfis Baixo/Médio/Alto. [Direção ambiental](../desenvolvimento-v2/docs/V2-04.md) |
| V2-05 · Combate | Guardião com aviso antes do impacto, perseguição, recuperação e retorno ao posto. Golpe, cometa, mana, recarga, interrupção, dano, esquiva, vitória e derrota. HUD de vida e mana. [Encontro jogável](../desenvolvimento-v2/docs/V2-05.md) |
| V2-06 · Elenco e aliado | 35 cartas distintas e modelos carregados sob demanda. IA com ordens Seguir, Manter posição e Atacar, navegação junto a obstáculos e verificação de alcance. [Inventário nominal dos 35](../desenvolvimento-v2/docs/V2-06.md) |
| V2-07 · Ambiente vivo | Travessia rasa com ondas e reação ao movimento, estado de umidade e secagem gradual. O passe posterior substituiu as lâminas simples por 56 touceiras com seis variações. Rochas receberam erosão assimétrica e as árvores próximas ganharam detalhe de tronco, raízes, galhos e copa. [Efeitos e limites](../desenvolvimento-v2/docs/V2-07.md) |
| Piloto da Trilha | Terreno próprio, ponte elevada, riacho, arcos, vegetação e cenário de avaliação do Archmage. A travessia automatizada chegou a z = −17,98. [Piloto visual](../desenvolvimento-v2/docs/V2-07_Piloto_Visual.md) |

### Produção dos personagens

As cartas originais orientam identidade, facção, cores, armas e silhueta. O manifesto individual de model sheets cobre 15 dos 35 personagens. Blender produz os GLBs e Babylon.js aplica os materiais e reproduz os clipes. O passe comum diferenciou pele, cabelo, penas, tecidos, metais e energia. Foram reexportados 34 modelos derivados e guardadas as versões anteriores em `desenvolvimento-v2/.local/roster-pre-realism`. [Passe do elenco](../desenvolvimento-v2/docs/V2-06_Passe_Realismo.md)

**Celestial Archmage.** A variante usada na floresta e na galeria conserva 29 articulações, oito encaixes e dez clipes — Idle, Walk, Run, Jump, Fall, Dodge, Cast, Strike, Hit e Defeat. A barba passou de 39 para 61 mechas e o cabelo ganhou 28 mechas laterais. Ouro e cristais receberam ajustes de superfície. A revisão no Chrome identificou olhos geométricos desproporcionais e a versão entregue conservou a expressão texturizada da referência. [Ficha da variante](../desenvolvimento-v2/docs/Premium_Archmage_v1.md) · [Fonte Blender](../desenvolvimento-v2/art/archmage-premium-v1.blend)

**Spirit Wolf — entrega mais recente.** O quadrúpede ganhou pernas mais longas, cabeça com a cor da pelagem, olhos espectrais estreitos e acabamento preto-azulado. No último passe foram modeladas 36 mechas na nuca e nos ombros, peitoral em V e cristal frontal. O GLB tem 1.104.544 bytes, 12 articulações e oito clipes — Idle, Walk, Run, Guard, Strike, Cast, Hit e Defeat. A inspeção frontal no Chrome mostra olhos e pingente legíveis à distância de jogo. Os sulcos repetitivos do pelo e o formato arredondado das patas continuam visíveis em close. [Modelo entregue](../desenvolvimento-v2/public/assets/spirit-wolf-premium-v1.glb) · [Captura real da galeria](../desenvolvimento-v2/.local/spirit-wolf-juba.jpg)

**Padrão visual.** “Premium v1” identifica variantes de trabalho. A fidelidade ultrarrealista desejada ainda exige anatomia, mãos ou patas, rostos, pelagem, penas, roupas e versões de detalhe por distância adequadas a cada personagem. Thunder Automaton e Solar Eagle já existem na galeria e são os estudos previstos para mecânica e asas.

### Ferramentas e organização

| Local na V2 | Conteúdo |
|---|---|
| `src/app`, `src/core`, `src/gameplay` | Ciclo da sessão, entrada, passo de simulação, controle, câmera, colisão, combate e IA. |
| `src/characters`, `src/world`, `src/rendering`, `src/ui` | Elenco e clipes, percursos, apresentação em Babylon.js e interface. |
| `art`, `public/assets` | Fontes Blender, geradores e recursos exportados para o navegador. |
| `tests`, `scripts`, `.local`, `docs` | Testes, perfis de desempenho, capturas, cópias de segurança e relatórios por entrega. |

**Unreal Engine 5.8.4.** O projeto isolado importou a versão de estudo do Archmage via FBX e registrou 37 recursos do personagem — uma malha, um esqueleto, dez animações e 25 materiais. Também foi salvo um mapa de apresentação com câmera e iluminação. A importação foi confirmada pelo editor em linha de comando usando cache em memória. A inspeção interativa desse mapa ficou pendente. A aplicação distribuída pelo servidor local roda em Babylon.js. O fluxo do lobo foi executado em Blender 5.3. [Estudo Unreal](../desenvolvimento-v2/docs/V2-08_Unreal_Lookdev.md)

### Verificação e desempenho

Na elaboração deste dossiê, `npm run test:unit` passou nos **30 testes** e `python scripts/snapshot.py verify` confirmou **421 arquivos e 39 entradas de backup**. Na última alteração do Spirit Wolf, o build, os cinco testes específicos do elenco e o teste no Chrome que carrega os 35 atores e leva um aliado à floresta passaram. A execução integral anterior de nove testes de navegador está registrada no V2-07. São execuções de momentos diferentes.

| Medição histórica no Chrome 157, 1280 × 720, Intel Iris Xe/D3D11 | FPS médio | p95 do intervalo entre quadros |
|---|---:|---:|
| Floresta, perfil Alto, corrida e giro | 60,0 | 16,9 ms |
| Combate com aliado, perfil Médio | 60,0 | 16,8 ms |
| Trilha, Archmage corrigido, travessia do arco | 60,0 | 16,9 ms |

As amostras representam esses percursos, após o carregamento, em tela de 60 Hz. Faltam medições na RTX 3060, em dispositivos móveis e do custo isolado da última alteração da juba. Para reproduzir a verificação técnica completa, execute `npm run ci` em `desenvolvimento-v2`.

### Situação da campanha e próximos marcos

O percurso permite explorar, comandar um aliado e vencer ou perder o encontro. Para fechar a primeira missão ainda faltam a ativação do portal de saída, o checkpoint persistente, a retomada e a recompensa concedida uma única vez. Essas entregas correspondem ao **V2-08 de progressão**. O relatório de estudo do Unreal usa o mesmo número no nome. O aceite do primeiro trecho jogável, a expansão para quatro mundos e a produção da campanha são etapas posteriores. Multiplayer permanece como suporte futuro.

O desenvolvimento descrito foi local. O repositório indicado para publicação futura é [caconeo/gamebeastmagic](https://github.com/caconeo/gamebeastmagic). A sequência de marcos e os critérios de aceite estão no [Plano Mestre V2](Game_Beast_Magic_V2_Plano_Mestre_Desenvolvimento.md).
