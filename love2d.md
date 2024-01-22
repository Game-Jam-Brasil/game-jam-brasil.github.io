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

Documentação resumida: <a href="https://www.lua.org/manual/5.4/manual.html#2.1">https://www.lua.org/manual/5.4/manual.html#2.1</a>

Lua suporta vários tipos básicos e strings, com tipagem fraca:

- nil para valores nulos
- boolean
- number (todos os números operam da mesma forma, podem ser tratados como inteiros ou floats/doubles dependendo do contexto e operações realizadas)
- function
- table (tabelas e estruturas em geral)
- userdata
- threads

#### Sintaxe básica

- comentários básicos usam dois hífens seguidos **--**
- atribuição com sinal de igual *=*
- comparação com
    - igualdade **==**
    - maior e menor  &gt; &lt;
    - diferença **~=** (til e igual)
    - negação **~**  (til)
- blocos (funções, ifs) terminam com **end**
- **if** não requer parênteses (é opcional), usar **then** após 
    - if valor == 10 then do_something() end
- não há switch/case, usa-se if/elseif encadeados
- for, while e repeat (do..while) são as

#### Escopo

Lua tem escopo **global** para variáveis e funções (basicamente, o inverso de python). Para usar o escopo local (que é recomendado, especialmente para variáveis dentro de funções), declare a variável como **local**:

```
function teste()
    local variavel = 10
    print(variavel)
end
```

#### Tabelas

Tabelas são a estrutura "tudo em um" da linguagem, funcionando como listas, coleções, hashmaps, "objetos" e estruturas. Fica na mão do desenvolvedor gerenciar o uso delas, de acordo com o contexto.

IMPORTANTE: tabelas indexadas tem índice inicial **um**, não zero como em outras linguagens. Operações com tabelas podem ser feitas diretas sobre os índices (similar à javascript) ou usando funções específicas (table.insert, table.remove, table.sort)

O tamanho de uma tabela pode ser obtido com o operador # (hashtag). Valores podem ser acessados pelo índice ou chaves (como em um hashtable). Tabelas podem conter quaisquer tipos de dados, inclusive outras tabelas. Loops podem ser usados para percorrer tabelas. No caso do acesso por chaves, as funções pairs e ipairs podem ser usadas.

Exemplo:

```
-- tabela simples, índices numéricos
local uma_tabela = {}
table.insert(uma_tabela, "Love2D")
table.insert(uma_tabela, 9.83)
table.insert(uma_tabela, false)

for i = 1, #uma_tabela do
    print(uma_tabela[i])
end

local outra_tabela = {}

outra_tabela["inicio"] = 1
outra_tabela["meio"] = 9
outra_tabela["fim"] = "Menu"

-- acessando como par de chave/valor. k contém a chave, v contém o valor (esses nomes podem ser diferentes)
for k,v in pairs(outra_tabela) do
    print(v)
end
```

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