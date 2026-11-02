# MUNDORA — Versão 1.6

**SEU MUNDO. SUAS CRIAÇÕES.**

Jogo web mobile de construção voxel (HTML5 + Three.js) para celulares Android na vertical.

## Publicação (GitHub Pages)
Envie o `index.html` para a raiz do repositório (substitui o anterior) e ative Pages em Settings > Pages.
Na primeira execução é preciso internet (o Three.js vem de um CDN). Se aparecer a versão antiga, recarregue sem cache.
Não apague os "dados do site" do navegador: é lá que ficam as cidades, construções e configurações salvas.

## Novidades da 1.6 (Minha Cidade)
Na parte inferior da construção da cidade: **BLOCOS · MINIATURAS · OBJETOS**.

**BLOCOS** — biblioteca organizada em categorias (Natureza, Pedra, Madeira, Tijolos, Concreto, Vidro, Decorativos, Escadas), com 51 materiais e 5 escadas:
grama, terra, pedra, areia (e vermelha), cascalho, madeira, tábuas (4 tipos), troncos (3), folhas (3), tijolos (3), tijolos de pedra, concreto em 15 cores, vidro (e 4 coloridos), estante, fardo de feno, ouro, ferro, tabuleiro e luminária.
Escadas (madeira clara, madeira escura, pedra, tijolos, concreto): degraus em 3D, 4 direções e modo invertido. A parte alta acompanha a direção da câmera; **GIRAR** e **INVERTER** na barra inferior ajustam a orientação.

**MINIATURAS** — mantida (pesquisa, prévia, posição, rotação, reutilização ilimitada).

**OBJETOS** — biblioteca independente: 5 camas coloridas, 4 postes (madeira, metálico, iluminação pública, decorativo), 4 portas e 8 janelas (vidro, molduras de madeira/branca/escura e vidros coloridos).
Escolha o objeto, arraste a prévia ou toque no mapa, **GIRAR** se quiser e **POSICIONAR**. Portas e janelas giram sozinhas para acompanhar a parede quando colocadas numa abertura (um buraco entre blocos). Toque num objeto para abrir/fechar a porta, acender/apagar o poste ou remover.

## Colisão
Voxel a voxel, considerando rotação: miniaturas só ocupam os blocos que realmente têm (os espaços vazios ficam livres); objetos e escadas ocupam suas células. Não é possível colocar blocos, miniaturas ou objetos em espaço ocupado. A prévia fica laranja e POSICIONAR fica desabilitado.

## Compatibilidade
Cidades, construções e configurações da 1.5 continuam abrindo sem alteração. Os objetos são gravados junto com a cidade (campo novo `objs`).
