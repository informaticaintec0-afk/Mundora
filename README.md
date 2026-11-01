# MUNDORA — Versão 1.5

**SEU MUNDO. SUAS CRIAÇÕES.**

Jogo web mobile de construção voxel (HTML5 + Three.js), pensado para celulares Android na vertical.

## Estrutura
- `index.html` — arquivo único com tudo: menu principal, telas internas e a Oficina (construtor 3D). Não há mais `menu.css` nem `menu.js`: se esses arquivos ainda existirem no seu repositório, pode apagá-los.

## Como publicar no GitHub Pages
1. Envie o `index.html` (substituindo o anterior) para a raiz do repositório.
2. Em Settings > Pages, escolha a branch e a pasta `/ (root)`.
3. Abra o endereço no Android. Se ainda aparecer a versão antiga, recarregue sem cache (ou limpe o cache do navegador; não apague os "dados do site", pois isso apaga as construções salvas).

Na primeira execução é preciso internet, pois o Three.js é carregado de um CDN.

## Fluxo
Abrir o jogo → Menu principal MUNDORA → escolher uma seção. A Oficina nunca abre sozinha: o estado inicial é sempre o menu, inclusive ao atualizar a página.

## Menu principal
- **Oficina**: o construtor livre de blocos 3D (mantém a sessão ao voltar ao menu).
- **Minha Cidade**: gerenciador de cidades (carregar, criar, excluir). Cada cidade é um mundo 3D vazio onde você constrói o terreno com blocos e posiciona suas construções salvas (veja a seção abaixo).
- **Minhas Criações**: lista todas as construções salvas (miniatura, nome, número de blocos, data), com **pesquisa por nome** (parcial, sem diferenciar maiúsculas nem acentos). Cada uma tem **Abrir na Oficina** e **Excluir**.
- **Configurações**: sombras, modo econômico, grade de construção e dicas na tela. Ficam salvas no aparelho.

O botão Voltar do Android retorna ao menu. Na Oficina, toque em "◀ VOLTAR" (canto superior esquerdo) para voltar ao menu principal.

## Controles da Oficina
- Toque rápido em uma face: coloca um bloco ao lado.
- Toque rápido no espaço vazio: coloca o primeiro bloco no plano de construção.
- Pressione e segure por aproximadamente meio segundo: quebra o bloco apontado.
- Arraste: gira a câmera.
- Pinça ou roda do mouse: zoom.
- Painel direito (▲ ◀ ▶ ▼): mantenha pressionado para deslocar a visão suavemente; ao soltar, o movimento para na hora.
- Botão central ✋: centraliza a câmera na construção (ou na origem, se estiver vazio).
- Barra inferior: seleciona o material.

- **Salvar**: pede um nome e grava na biblioteca (Minhas Criações) com miniatura. Se a construção já foi salva antes, pergunta se deseja **Atualizar** a existente ou **Salvar como nova cópia** — nada é sobrescrito em silêncio.
- **Carregar**: leva a Minhas Criações, onde você escolhe qual construção abrir. Se a Oficina tiver alterações não salvas, o jogo pede confirmação antes de substituí-las.
- **Novo**: se a construção tem alterações não salvas, abre uma janela com três opções: *Salvar e começar novo projeto*, *Descartar e começar novo projeto* ou *Cancelar* (volta à construção atual sem mudar nada). Se a Oficina está vazia, ou se não há alterações desde o último salvamento, começa o novo projeto direto.

## Excluir uma criação
Toque em **Excluir** no cartão da construção. O jogo pergunta "Deseja realmente excluir esta construção?" com **CANCELAR** e **EXCLUIR**. Cancelar não muda nada. Excluir remove somente aquela construção da biblioteca e atualiza a lista na hora. **As cópias dela que já estão na Minha Cidade continuam no mapa** (a cidade guarda sua própria cópia dos blocos).

## Minha Cidade
**Gerenciador (ao tocar em MINHA CIDADE no menu):** três botões.
- **CARREGAR CIDADE:** lista as cidades salvas (nome, pré-visualização, blocos, construções, data). Toque em **Abrir** para continuar de onde parou.
- **CRIAR NOVA CIDADE:** pede um nome (não aceita vazio nem repetido) e cria um mundo **completamente vazio**. Nada é copiado de outras cidades.
- **EXCLUIR CIDADE:** lista as cidades; **Excluir** pede confirmação com o nome da cidade (**CANCELAR** / **EXCLUIR**). Só aquela cidade é apagada.

**Editor da cidade:** o mapa 3D ocupa quase toda a tela. Embaixo ficam os dois botões grandes **BLOCOS** e **MINIATURAS**; cada um abre um painel que ocupa só parte da tela e fecha com **✕ Fechar** (a seleção não se perde).
- **Mundo vazio:** não existe chão, plataforma nem terreno automático. Uma grade discreta (no nível de construção), uma moldura dos limites do mundo e uma marca da origem servem de referência, sem criar blocos. O mundo vai de −64 a 63 em largura e comprimento, e de −16 a 47 de altura.
- **BLOCOS:** os mesmos 11 materiais e texturas pixeladas da Oficina. Escolher um material ativa a construção: **toque** coloca um bloco (no nível de construção, ou encostado na face do bloco tocado: em cima, ao lado), **segurar** remove, **arrastar** gira a câmera. **▲ ▼** mudam o nível de construção (para fazer chão, paredes, elevações, plataformas e depressões em qualquer altura). Ferramentas: **Selecionar** (seleciona construções colocadas) e **Remover bloco** (toque remove).
- **MINIATURAS:** as construções da Oficina, com pesquisa por nome. Tocar numa mostra a **prévia transparente**: mova arrastando, tocando no mapa ou pelas setas "mover prévia"; **⟳ GIRAR** (90° por toque); **▲ ▼** ajustam a altura. A prévia senta sozinha no ponto mais alto do terreno sob ela. O contorno fica verde (ou laranja se sobrepuser outra construção, o que é permitido). **POSICIONAR** pede confirmação (**CANCELAR** / **CONFIRMAR**).
- **Cópias ilimitadas:** a mesma miniatura pode ser usada quantas vezes quiser; cada cópia é independente e a original nunca sai da Oficina. Para remover uma cópia: ferramenta Selecionar, toque na construção e **REMOVER** (a original continua em Minhas Criações).
- **Câmera:** arrastar gira, pinça (ou ＋/－) dá zoom, setas movem o mapa (contínuo) e ✋ centraliza. A câmera acompanha o nível de construção.
- **Salvamento automático:** cada alteração é salva sozinha (blocos logo após editar, construções na hora, tudo ao sair). Ao fechar e abrir o jogo, a cidade volta exatamente como estava. Se a memória do aparelho estiver cheia, o jogo avisa.
- **Desempenho:** o terreno é dividido em pedaços de 16×16×16; cada pedaço vira uma única malha só com as faces visíveis, e só os pedaços alterados são refeitos. O mapa só é redesenhado quando algo muda.

## Visual dos blocos
Todos os materiais usam texturas pixeladas de 16×16 pixels no estilo clássico, com filtro de pixels nítidos (sem suavização). Cada face do bloco mostra uma textura que se repete continuamente entre blocos vizinhos.
- **Grama**: topo verde, laterais de grama sobre terra e base de terra.
- **Madeira**: tronco com casca nas laterais e anéis no topo e na base.
- **Tábuas, Tijolo, Terra, Pedra, Areia, Folhas, Branco, Preto**: texturas próprias; **Vidro** é translúcido com borda clara.
- As texturas são desenhadas por código (não há arquivos de imagem), e as mesmas aparecem na barra de materiais e nas miniaturas de Minhas Criações.
- Miniaturas salvas em versões anteriores são redesenhadas com as texturas na primeira vez que Minhas Criações é aberta (a data da construção não muda).

## Armazenamento
- A biblioteca fica na chave `mundora_library` do navegador: lista de `{id, nome, blocos, miniatura, criado, atualizado}`.
- As cidades ficam em `mundora_cities` (índice: nome, datas, contagens, pré-visualização) e uma chave por cidade, `mundora_cd_<id>`, com `blocks` (comprimido em trechos `[y, z, tipo, x inicial, quantidade]`), `defs` (cópia dos blocos de cada construção usada) e `items` (`{id, cid, def, x, y, z, rot}`). Excluir uma cidade remove só a sua chave.
- A cidade única da versão 1.4 é migrada, na primeira abertura, para uma cidade chamada "Minha Cidade". Como ela tinha um chão fixo invisível ao código, esse chão vira blocos de grama reais (48×48), para as construções continuarem apoiadas. A chave antiga não é apagada.
- Na primeira abertura da v1.2, a construção do formato antigo (`construtor_blocos_save`) é copiada para a biblioteca como "Construção salva". A chave antiga **não é apagada**.

## Limitações desta versão
- Minhas Criações ainda não tem renomear (Etapa 2).
- Minha Cidade ainda não tem moradores (NPCs), ciclo de dia e noite, nem mover uma construção já posicionada (para mudar de lugar: remova e posicione de novo). Também não há desfazer para blocos.
- Uma construção posicionada guarda os blocos do momento em que foi colocada. Se você atualizar a original na Oficina, as cópias antigas não mudam; novas cópias usam a versão nova.
- A biblioteca fica no armazenamento do navegador e pode ser apagada se os dados do site forem limpos.
- Requer internet na primeira execução para baixar o Three.js (será embutido em uma etapa futura).
