# Love2D

Love2D é uma engine/framework para jogos que usa a linguagem Lua para programação. Suporta boa parte das ações necessárias para jogos.

- inicialização e loop de gameplay com delta time (love.init e love.update);
- desenho de imagens e primitivas (love.draw), com opção de recorte para spritesheets (clipping, com quad) e composição (canvas);
- primitivas variadas (círculos, retângulos, polígonos, etc);
- carregamento e uso de assets (imagens, áudio, fontes);
- suporte a input, com funções prontas para verificações diversas (via sdl):
    - suporte à teclado e mouse
    - suporte à joysticks, com opções de mapeamento
    - verificar se tecla, botões do mouse e controles está pressionado no update (ex: love.keyboard.isDown)
    - callbacks para pressionar e soltar teclas (love.keypressed, love.keypressed)
- operações visuais como transladação, escala e rotação (translate, scale e rotate)
- bom desempenho para jogos 2D simples


## Observações gerais sobre a linguagem Lua

Documentação bem resumida: https://www.lua.org/manual/5.4/manual.html#2.1 

Lua suporta vários tipos básicos e strings, com tipagem fraca:

- nil para valores nulos
- boolean
- number (todos os números operam da mesma forma, podem ser tratados como inteiros ou floats/doubles dependendo do contexto e operações realizadas)
- function
- table (tabelas e estruturas em geral)
- userdata
- threads


#### Escopo

Lua tem escopo **global** para variáveis e funções (basicamente, o inverso de python). Para usar o escopo local (que é recomendado, especialmente para variáveis dentro de funções), declare a variável como **local**:

```
function teste()
    local varivel = 10
end
```

#### Tabelas

Tabelas são a estrutura "tudo em um" da linguagem, funcionando como listas, coleções, hashmaps, "objetos" e estruturas. Fica na mão do desenvolvedor gerenciar o uso delas, de acordo com o contexto.

IMPORTANTE: tabelas indexadas tem índice inicial **um**, não zero como em outras linguagens. Operações com tabelas podem ser feitas diretas sobre os índices (similar à javascript) ou usando funções específicas (table.insert, table.remove, table.sort)

#### Suporte à orientação a objetos

Lua é uma linguagem multi-paradigma, puxando para o lado funcional (similar Python). Há várias opções para usar a linguagem, e suporte "indireto" à orientação à objetos. Dá para programar em uma forma similar à OO tradicional diretamente na linguagem, ou usar bibliotecas que facilitam essa operação (ver na lista abaixo de bibliotecas para Love2D).

## Observações gerais sobre a Love2D

#### Rodando e gerando executáveis

Os projetos podem rodar de algumas formas:

- diretamente a partir do executável love.exe, apontando para a pasta que contém o main.lua
- criando arquivos compactados (zip) com extensão love
- gerando executáveis simples (combinando o love.exe com a pasta zipada contendo o main.lua)

#### Suporte à web é limitado




Links gerais:

- <a href="https://github.com/love2d-community/awesome-love2d" target="_blank">https://github.com/love2d-community/awesome-love2d</a> : lista de bibliotecas, projetos e outros recursos sobre a Love2D, tais como:

- bibliotecas para gerenciar cenas/fases
- suporte à orientação de objetos