# MUNDORA — Versão 1.4

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
- **Minha Cidade**: mapa 3D plano onde você posiciona suas construções salvas (veja a seção abaixo).
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
- **Mapa:** chão plano de 48×48 células, com o mesmo estilo de blocos do jogo, inicialmente vazio.
- **Câmera:** arraste para girar, pinça (ou botões ＋/－) para aproximar e afastar, setas para mover o mapa (continuam enquanto pressionadas) e ✋ para centralizar.
- **Biblioteca (embaixo):** miniaturas das construções salvas, com barra de pesquisa pelo nome.
- **Posicionar:** toque numa miniatura para ver a **prévia transparente** no mapa. Mova arrastando a prévia, tocando no mapa ou com as setas "mover prévia" (1 célula por toque). **⟳ GIRAR** gira de 90° em 90°. O contorno fica verde, ou laranja se a prévia sobrepuser outra construção (é permitido). **POSICIONAR** pede "Deseja realmente colocar esta construção aqui?" com **CANCELAR** e **CONFIRMAR**.
- **Cópias ilimitadas:** a mesma construção pode ser colocada quantas vezes quiser. Cada cópia é independente e a miniatura nunca sai da biblioteca.
- **Remover do mapa:** toque numa construção posicionada, depois em **REMOVER** (com confirmação). Isso não apaga a original da biblioteca.
- **Salvamento automático:** cada construção posicionada ou removida é salva na hora. Ao fechar e abrir o jogo, a cidade continua como foi deixada. Se a memória do aparelho estiver cheia, o jogo avisa e não posiciona (nunca fica diferente do que está salvo).
- **Desempenho:** cada construção vira uma única malha com apenas as faces visíveis, e o mapa só é redesenhado quando algo muda.

## Visual dos blocos
Todos os materiais usam texturas pixeladas de 16×16 pixels no estilo clássico, com filtro de pixels nítidos (sem suavização). Cada face do bloco mostra uma textura que se repete continuamente entre blocos vizinhos.
- **Grama**: topo verde, laterais de grama sobre terra e base de terra.
- **Madeira**: tronco com casca nas laterais e anéis no topo e na base.
- **Tábuas, Tijolo, Terra, Pedra, Areia, Folhas, Branco, Preto**: texturas próprias; **Vidro** é translúcido com borda clara.
- As texturas são desenhadas por código (não há arquivos de imagem), e as mesmas aparecem na barra de materiais e nas miniaturas de Minhas Criações.
- Miniaturas salvas em versões anteriores são redesenhadas com as texturas na primeira vez que Minhas Criações é aberta (a data da construção não muda).

## Armazenamento
- A biblioteca fica na chave `mundora_library` do navegador: lista de `{id, nome, blocos, miniatura, criado, atualizado}`.
- A cidade fica na chave `mundora_city`: `{defs, items}`. Cada item guarda `{id, cid (construção original), def, x, z, rot (0 a 3, giros de 90°)}`; `defs` guarda a cópia dos blocos (compartilhada entre cópias idênticas).
- Na primeira abertura da v1.2, a construção do formato antigo (`construtor_blocos_save`) é copiada para a biblioteca como "Construção salva". A chave antiga **não é apagada**.

## Limitações desta versão
- Minhas Criações ainda não tem renomear (Etapa 2).
- Minha Cidade ainda não tem moradores (NPCs), ciclo de dia e noite nem mover uma construção já posicionada (para mudar de lugar: remova e posicione de novo).
- Uma construção posicionada guarda os blocos do momento em que foi colocada. Se você atualizar a original na Oficina, as cópias antigas não mudam; novas cópias usam a versão nova.
- A biblioteca fica no armazenamento do navegador e pode ser apagada se os dados do site forem limpos.
- Requer internet na primeira execução para baixar o Three.js (será embutido em uma etapa futura).
