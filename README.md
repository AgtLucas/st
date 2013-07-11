### Missão

Repassar algumas dicas, truques, macetes, cheats, bruxarias, magias negra, enfim, qualquer coisa que possa tornar o já produtivo Sublime Text 2 ainda melhor...

Referências você pode encontrar no final da página, caso eu não esqueça de adicionar.

Chega de blabla,

```javascript
var ST2 = "Sublime Text 2";
```

Ah, para prosseguir, certifique-se que tenha o ST2 (ou o ST3 Beta) instalado. (Oh rly?)

### Package Control

Se você usa o ST2 sem o Package Control você não sabe o que está perdendo, sério, o Package Control é um gerenciador de pacotes ultra mega power super duper kamen rider black RX recomendado, com ele você pode instalar plugins e pacotes que para tornar o ST2 ainda melhor.

Para instalar o Package Control, é muito simples:

* [Clique aqui](http://wbond.net/sublime_packages/package_control)
* Clique no botão nada chamativo "Install Open Source"
* Copie o conteúdo que é gerado:

```
import urllib2,os; pf='Package Control.sublime-package'; ipp=sublime.installed_packages_path(); os.makedirs(ipp) if not os.path.exists(ipp) else None; urllib2.install_opener(urllib2.build_opener(urllib2.ProxyHandler())); open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read()); print('Please restart Sublime Text to finish installation')
```

* Abra o ST2
* Pressione `CTRL + ^` para abrir o console
* Cole o conteúdo copiado anteriormente e pressione `ENTER`
* Espere o processo acabar e certifique-se de reiniciar o ST2
* That's All Folks!

Pronto, Package Control instalado, agora é só testar instalando algum plugin ou algo do tipo, para isso:

* Por exemplo, vamos instalar o [emmet](http://emmet.io/)
* `CMD + SHIFT + P` ou `CTRL + SHIFT + P`
* Digite `Install Package` e aperte `ENTER`
* Na caixa de texto que abrir, digite `Emmet` e aperte `ENTER`
* Espere o download acabar conforme mostra a barra de status no canto inferior esquerdo do ST2
* E pronto, mais rápido que miojo (claro, depende da internet e do tamanho do plugin)

O Emmet é meu plugin preferido, você vai entender o motivo [clicando aqui](http://docs.emmet.io/cheat-sheet/)

### Múltiplos cursores

Imagine a seguinte situação, digamos que você tenha este pedaço de código:

```html
<ul class="foo">
  <li class="bar"></li>
  <li class="bar"></li>
  <li class="bar"></li>
  <li class="bar"></li>
  <li class="bar"></li>
  <li class="bar"></li>
  <li class="bar"></li>
  <li class="bar"></li>
  <li class="bar"></li>
  <li class="bar"></li>
</ul>
```

E por algum motivo mais bizarro que ter `<li>` com classes com nomes escrotos, você precisa trocar o nome das classes de `bar` para, sei lá, `buteco` ????? Anyway, um simples `search and replace` resolveria o problema, porém, podemos fazer isso de outra forma.

* Coloque o cursor do rato (ora pois) sobre a palavra desejada
* E... `CMD + D` ou `CTRL + D`
* Você vai notar que vai selecionar a primeira palavra, e se você repetir o comando, vai selecionar a próxima, e assim por diante
* Se você for mais pregui.. digo, se você for uma pessoa que procura maximizar a produtividade, `CTRL + CMD + G` e veja a mágica

### Snippets

Os malditos e viciantes snippets, pois bem, se você instalou o Emmet, é óbvio que notou que o mesmo nada mais é do que um plugin de snippets, porém, e se você quiser snippets para PHP, Python, Ruby, Go, etc? Bom, você pode procurar algum plugin usando o Package Control, ou, você pode criar o seu próprio snippet! (Oh rly?)

Para isso:

* Tools > New Snippet
* Um novo documento será aberto com o seguinte conteúdo XML:

```python
<snippet>
  <content><![CDATA[
Hello, ${1:this} is a ${2:snippet}.
]]></content>
  <!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
  <!-- <tabTrigger>hello</tabTrigger> -->
  <!-- Optional: Set a scope to limit where the snippet will trigger -->
  <!-- <scope>source.python</scope> -->
</snippet>
```
Antes de criarmos um snippet, explicar rapidamente o conteúdo acima é preciso, para entendimento termos

* O snippet deve ficar entre as tags `<content><![CDATA[ ]]></content>`
* (OPCIONAL) Descomentar (sic) `<!-- <tabTrigger>hello</tabTrigger> -->` e ali setar o atalho que vamos digitar para fazer o snippet funcionar
* (OPICIONAL) Você pode descomentar (sic) a tag `<scope></scope>` e definir um escopo de extensão onde seu snippet ficará acessível, no exemplo temos `source.python`, ou seja, o snippet ficaria acessível apenas em arquivos Python

Vamos criar um snippet PHP para o WordPress, que tem como objetivo "remover" o jQuery injetado pelo WordPress e registrarmos o jQuery CDN do Google

```python
<snippet>
  <content><![CDATA[
if ( !is_admin() ) {
  wp_deregister_script( 'jquery' );
  wp_register_script( 'jquery', "http" . ($_SERVER['SERVER_PORT'] == 443 ? "s" : "") . "://ajax.googleapis.com/ajax/libs/jquery/$1/jquery.min.js", false, null, true );
  wp_enqueue_script( 'jquery' );
}
]]></content>
  <!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
  <tabTrigger>wkj</tabTrigger>
  <!-- Optional: Set a scope to limit where the snippet will trigger -->
  <scope>source.php</scope>
</snippet>
```

* Note essa parte `://ajax.googleapis.com/ajax/libs/jquery/$1/jquery.min.js", false, null, true );`, o `$1` é para que você defina qual versão do jQuery deseja usar, automaticamente após o snippet ser criado o cursor estará naquela posição
* Quando estiver pronto, `CMD + S` ou `CTRL + S` para salvar
* O ST2 vai indicar onde salvar o snippet, no OS X o caminho é: `Library/Application \ Support/Sublime \ Text \ 2/Packages/User`
* Você pode criar uma pasta nesse diretório com o nome da linguagem do snippet, assim, você terá um maior controle e organização dos snippets
* IMPORTANTE: Escolha um nome de fácil entendimento e salve com a extensão `.sublime-snippet`
* É isso, agora toda vez que eu quiser "matar" o jQuery inserido pelo WordPress em algum tema e registrar um jQuery via CDN, digito `wkj` e pressiono `TAB`

Acredito que isso cobre o básico sobre snippets, e como é um assunto um pouco mais complexo, sugiro que se tiveres interesse, leia [este link](http://sublimetext.info/docs/en/extensibility/snippets.html).

Vale lembrar que o ST2 já tem vários snippets default, para checar: `CMD + SHIFT + P` ou `CTRL + SHIFT + P` e digite `snippet`.

### Atalhos

No ST2 temos vários atalhos para agilizar nosso workflow, abaixo vou listar os básicos:

* `CMD + SHIFT + P` ou `CTRL + SHIFT + P`: Paleta de comandos
* `CMD + /` ou `CTRL + /`: Comenta ou "descomenta"
* `CMD + SHIFT + /` ou `CTRL + SHIFT + /`: Bloco de comentário
* `CMD + P` ou `CTRL + P`: Vai para qualquer lugar, você pode usar este comando para abrir um arquivo que está no diretório do seu projeto, por exemplo
* `CTRL + G`: Vai para linha tal
* `CMD + K,C` ou `CTRL + K,C`: Vai para onde o cursor está
* `CMD + K,B` ou `CTRL + K,B`: Mostra ou esconde a sidebar
* `CMD + F` ou `CTRL + F`: Nem vou falar o que faz
* `CMD + K,U` ou `CTRL + K,U`: Converte a seleção para `uppercase`
* `CMD + K,L` ou `CTRL + K,L`: Converte a seleção para `lowercase`
* `CMD + W` ou `CTRL + W`: Fecha a aba

### Criando arquivos e pastas de maneira + eficiente

Uma das coisas que realmente não gosto no ST2, é a maneira como a criação de arquivos e pastas deve ser feita, acho meio chato `CMD + N` ou `CTRL + N` para criar um novo arquivo, salvar, escolher o nome e a pasta, e para criar uma nova pasta quase a mesma coisa.
Porém, existe um plugin (sempre um plugin) para nos ajudar, o nome dele é `Advanced New File`. Para instalar é a mesma coisa, mesmo processo explicado lá no começo.

Para usar:

* `CMD + OPTION + N` ou `CTRL + ALT + N` e digitar o nome do arquivo ou da pasta que você deseja
* Por exemplo, se você digitar: `style.sass`, um arquivo com este nome será criado no root do projeto
* Se você digitar: `sass/style.sass`, um arquivo com este nome será criado dentro da pasta `sass`,
* Se você digitar: `sass/`, uma pasta com este nome vai ser criado no root do seu projeto (a não ser que ela já exista)

Done.

### Plugins e outras coisas

Alguns plugins, Color Schemes e temas que uso e acho interessante

* Sidebar Enhancements: Excelente plugin que adiciona opções extras na sidebar do ST2
* Sublime Code Intel: Autocomplete eficiente
* Theme Soda: Um tema bacana e completo
* Dayle Rees Color Schemes: Na minha opinião, o melhor pacote de esquema de cores para o ST2
* PHP Syntax Checker: Impede que o arquivo seja salvo se o mesmo tiver erro de sintaxe


***

Chega por hoje!

Espero que isso seja útil, e se eu tiver vontade ou descobrir alguma coisa relevante que poderia estar aqui, ou ainda, se esqueci de alguma coisa, editarei.

### Referências

* [Sublime Text 2 Documentation](http://www.sublimetext.com/docs/2/)
* [Perfect Workflow in Sublime Text 2](https://tutsplus.com/course/improve-workflow-in-sublime-text-2/)

## Licença

```
= I DON'T CARE

USE DA FORMA QUE QUISER, POR SUA CONTA E RISCO.
FIQUE A VONTADE PARA COPIAR, REPLICAR O CONTEÚDO AQUI DESCRITO, NÃO PRECISA NEM CITAR A FONTE, SE ISSO VAI AJUDAR ALGUÉM DE ALGUMA FORMA JÁ ESTÁ VALENDO.
```
Exceto os links citados nesta página.
