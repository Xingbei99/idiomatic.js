# Princípios para Escrever Javascript de forma Consistente e Idiomática

## Este é um documento vivo e novas idéias para melhorar os códigos correspondentes são sempre bem vindas. Contribua: faça fork, clone, branch, commit, push, pull request.

* Rick Waldron [@rwaldron](http://twitter.com/rwaldron), [github](https://github.com/rwldrn)
* Mathias Bynens [@mathias](http://twitter.com/mathias), [github](https://github.com/mathiasbynens)
* Schalk Neethling [@ossreleasefeed](http://twitter.com/ossreleasefeed), [github](https://github.com/ossreleasefeed/)
* Kit Cambridge  [@kitcambridge](http://twitter.com/kitcambridge), [github](https://github.com/kitcambridge)
* Raynos  [github](https://github.com/Raynos)
* Matias Arriola [@MatiasArriola](https://twitter.com/MatiasArriola), [github](https://github.com/MatiasArriola/)
* Idan Gazit [@idangazit](http://twitter.com/idangazit), [github](https://github.com/idangazit)
* Leo Balter [@leobalter](http://twitter.com/leobalter), [github](https://github.com/leobalter)

## Todo código em qualquer aplicação deve parecer como se fosse escrito por uma única pessoa, independente de quantas pessoas tenham contribuído.

### A lista a seguir descreve as práticas que eu uso em todo código onde sou o autor original; contribuições em projetos que eu criei devem seguir essas mesmas orientações.

### Eu não tenho a intenção de impor minhas preferências por estilos nos códigos de outras pessoas; se eles seguem um estilo em comum - isso deve ser respeitado.

> "Parte de ser um bom gestor de um projeto bem sucedido é perceber que escrever código para si mesmo é uma má idéia™. Se milhares de pessoas estão utilizando o seu código, então escreva o seu código com máxima clareza, não sob a sua preferência pessoal sobre como ser esperto com uma especificação." - Idan Gazit

## Traduções

* [French](https://github.com/jfroffice/idiomatic.js/)
* [Spanish](https://github.com/MatiasArriola/idiomatic.js/)
* [Português - Brasil](https://github.com/leobalter/idiomatic.js/)


## Conteúdo Importante e Não Idiomático:

### Qualidade de Código: Ferramentas, Recursos e Referências Bacanas

 * [jsPerf](http://jsperf.com/)
 * [jsFiddle](http://jsfiddle.net/)
 * [jsbin](http://jsbin.com/)
 * [JavaScript Lint (JSL)](http://javascriptlint.com/)
 * [jshint](http://jshint.com/)
 * [jslint](http://jslint.org/)

[Leveraging Code Quality Tools (em pt_BR: Aproveitamento de Ferramentas de Qualidade de Código) por Anton Kovalyov](http://anton.kovalyov.net/slides/gothamjs/)


### Fique Ligado

[http://es5.github.com/](http://es5.github.com/)

Deve ser considerado o seguinte: 1) incompleto; e 2) *LEITURA OBRIGATÓRIA*. Eu não concordo sempre com os estilos escritos pelos autores abaixo, mas uma coisa é certa: Eles são consistentes. Além disso, esses são autoridades na linguagem.

 * [Eloquent JavaScript](http://eloquentjavascript.net/)
 * [JavaScript, JavaScript](http://javascriptweblog.wordpress.com/)
 * [Rebecca Murphey](http://www.rebeccamurphey.com/) or [Adventures in JavaScript Development](http://rmurphey.com/)
 * [Perfection Kills](http://perfectionkills.com/)
 * [Douglas Crockford's Wrrrld Wide Web](http://www.crockford.com)


### Processos de Build e Deploy

Projetos devem sempre tentar incluir alguns formatos genéricos para que o código fonte possa ser compactado no preparo para uso em produção. Algumas ferramentas populares e testadas incluem o [Uglify.js](https://github.com/mishoo/UglifyJS) feito em JavaScript, assim como o [Google Closure Compiler](http://code.google.com/closure/compiler/) e [YUI Compressor](http://developer.yahoo.com/yui/compressor/) feitos em Java. Escolha um e apoie o mesmo.

Você pode encontrar um "build kit" funcional e genérico no diretório `/kits` deste repositório. A Utilização é simples: 1) copie o conteúdo de um dos kits encontrados em `/kits` para um novo diretório, 2) grave o arquivo .js de  seu projeto no diretório `/src`, 3) coloque o nome do projeto dentro de `project.txt`, 4) execute o `make` pela linha de comando. (Caminho mais fácil: troque as ocorrências de "foo")


### Ambiente de Teste

Projetos _devem_ incluir alguma forma de teste unitário, por referência, de implementaçao ou funcional. Demonstrações de casos de uso NÃO SE QUALIFICAM como "testes". A lista a seguir contém frameworks de testes, nenhuma delas é considerada melhor que as demais.

 * [QUnit](http://github.com/jquery/qunit)
 * [Jasmine](https://github.com/pivotal/jasmine)
 * [Vows](https://github.com/cloudhead/vows)
 * [Mocha](https://github.com/visionmedia/mocha)
 * [Hiro](http://hirojs.com/)
 * [JsTestDriver](https://code.google.com/p/js-test-driver/)

## Tabela de Conteúdos

 * [Espaço em Branco](#whitespace)
 * [Sintaxe Bonita](#spacing)
 * [Checagem de Escrita (Cortesia das Recomendações de Estilo do Núcleo do jQuery)](#type)
 * [Avaliação Condicional](#cond)
 * [Estilo Prático](#practical)
 * [Nomenclatura](#naming)
 * [Miscelâneas](#misc)
 * [Objetos Nativos e Hospedados](#native)
 * [Comentários](#comments)


## Manifesto de Estilo Idiomático


1. <a name="whitespace">Espaço em Branco</a>

	* Nunca misture espaços e tabs.
 	* Quando começar um projeto, antes de escrever qualquer código, escolha entre indentação suave (espaços) ou tabulação real (tabs) - isso é lei.
		* Pela legibilidade, eu sempre recomendo que configure o tamanho de indentação de seu editor para dois caracteres - isso significa dois espaços ou dois espaços representando um tab real.
	* Se o seu editor suportar, sempre trabalhe com a configuração de "mostrar caracteres invisíveis" ligada. Os benefícios desta prática são:
		* Fortalecer a consistência
		* Eliminação de espaço em branco ao final da linha
		* Eliminação de espaços em uma linha em branco
		* Leituras de commits e diffs ficam mais legíveis


2. <a name="spacing">Sintaxe Bonita</a>

	A. Parênteses, Chaves e Quebras de Linhas

	```javascript

	// if/else/for/while/try sempre tem espaços, chaves e ocorrem em múltiplas linhas
	// isso facilita a legibilidade

	// 2.A.1.1
	// Exemplos de código pouco claro/bagunçado

	if(condicao) facaAlgo();

	while(condicao) iteracao++;

	for(var i=0;i<100;i++) algumaIteracao();


	// 2.A.1.1
	// Use espaço em branco para facilitar a leitura

	if ( condicao ) {
		// instruções
	}

	while ( condicao ) {
		// instruções
	}

	for ( var i = 0; i < 100; i++ ) {
		// instruções
	}

	// Ainda melhor:

	var i,
		length = 100;

	for ( i = 0; i < length; i++ ) {
		// instruções
	}

	// Ou...

	var i = 0,
		length = 100;

	for ( ; i < length; i++ ) {
		// instruções
	}

	var prop;

	for ( prop in object ) {
		// instruções
	}


	if ( true ) {
		// instruções
	} else {
		// instruções
	}
	```


	B. Atribuições, Declarações, Funções ( Nomenclatura, Expressão, Construtor )

	```javascript

	// 2.B.1.1
	// Variáveis
	var foo = "bar",
		num = 1,
		undef;

	// Notações Literais:
	var array = [],
		object = {};


	// 2.B.1.2
	// Utilizando apenas um `var` por escopo (função) promove legibilidade
	// e mantém a sua lista de declaração livre de desordem (além de evitar algumas tecladas)
	
	// Ruim
	var foo = "";
	var bar = "";
	var qux;

	// Bom
	var foo = "",
		bar = "",
		quux;

	// ou..
	var // comentário aqui
	foo = "",
	bar = "",
	quux;

	```

	```javascript

	// 2.B.2.1
	// Declaração de Função Nomeada
	function foo( arg1, argN ) {

	}

	// Utilização
	foo( arg1, argN );


	// 2.B.2.2
	// Declaração de Função Nomeada
	function square( number ) {
		return number * number;
	}

	// Utilização
	square( 10 );

	// Estilo de passagem artificialmente contínua
	function square( number, callback ) {
		callback( number * number );
	}

	square( 10, function( square ) {
		// instruções de callback
	});


	// 2.B.2.3
	// Expressão de Função
	var square = function( number ) {
		// Retorna algo de valor e relevante
		return number * number;
	};

	// Expressão de Função com Identificador
	// Esse formato preferencial tem o valor adicional de permitir
	// chamar a si mesmo e ter uma identidade na pilha de comandos:
	var factorial = function factorial( number ) {
		if ( number < 2 ) {
			return 1;
		}

		return number * factorial( number-1 );
	};


	// 2.B.2.4
	// Declaração de Construtor
	function FooBar( options ) {

		this.options = options;
	}

	// Utilização
	var fooBar = new FooBar({ a: "alpha" });

	fooBar.options;
	// { a: "alpha" }

	```


	C. Exceções, Pequenos Desvios

	```javascript

	// 2.C.1.1
	// Funções com callbacks
	foo(function() {
		// Veja que não há espaço extra entre o primeiro parentesis
		// da chamada de função e a palavra "function"
	});

	// Função recebendo uma array, sem espaço
	foo([ "alpha", "beta" ]);

	// 2.C.1.2
	// Função recebendo um objeto, sem espaço
	foo({
		a: "alpha",
		b: "beta"
	});

	// Parêntesis internos de agrupamento, sem espaço
	if ( !("foo" in obj) ) {

	}

	```

	D. Consistência Sempre Ganha

	Nas seções 2.A-2.C, as regras de espaço em branco são recomendadas sob um propósito simples e maior: consistência.
	É importante notar que preferências de formatação, tais como "espaço em branco interno" deve ser considerado opcional, mas apenas um estilo deve existir por toda a fonte de seu projeto.

	```javascript

	// 2.D.1.1

	if (condition) {
		// instruções
	}

	while (condition) {
		// instruções
	}

	for (var i = 0; i < 100; i++) {
		// instruções
	}

	if (true) {
		// instruções
	} else {
		// instruções
	}

	```

	E. Finais de Linha e Linhas Vazias

	Espaços em branco podem arruinar diffs e fazer com que _changesets_ sejam impossíveis de se ler. Considere incorporar um gancho de pre-commit que remova espaços em branco ao final das linhas e espaços em branco em linhas vazias automaticamente.

3. <a name="type">Checagem de Escrita (CCortesia das Recomendações de Estilo do Núcleo do jQuery)</a>

	3.A Tipos Existentes 

	* String:

		`typeof variable === "string"`

	* Number:

		`typeof variable === "number"`

	* Boolean:

		`typeof variable === "boolean"`

	* Object:

		`typeof variable === "object"`

	* Array:

		`Array.isArray(arrayObject)`
		(wherever possible)

	* null:

		`variable === null`

	* null ou undefined:

		`variable == null`

	* undefined:

		* Variáveis Globais:

			* `typeof variable === "undefined"`

		* Variáveis Locais:

			* `variable === undefined`

		* Propriedades:
			* `object.prop === undefined`
			* `object.hasOwnProperty( prop )`
			* `"prop" in object`


	JavaScript é uma linguagem de escrita dinâmica - o que pode ser seu melhor amigo ou pior inimigo, então: Sempre respeite o `tipo`, como recomendado.


	3.B Tipos Coagidos

	Considere as implicações do seguinte...

	Dado este HTML:

	```html

	<input type="text" id="foo-input" value="1">

	```


	```js

	// 3.B.1.1

	// `foo` foi declarado com o valor `0` e seu tipo é `number`
	var foo = 0;

	// typeof foo;
	// "number"
	...

	// Algum momento depois no seu código, você precisa atualizar `foo`
	// com um novo valor derivado de um elemento `input`

	foo = document.getElementById("foo-input").value;

	// Se você testasse `typeof foo` agora, o resultado seria uma `string`
	// Isso significa que se tivesse uma lógica que testasse `foo` como:

	if ( foo === 1 ) {

		importantTask();

	}

	// `importantTask()` nunca seria chamado, mesmo que `foo` tivesse um valor "1"


	// 3.B.1.2

	// Você pode prevenir problemas utilizando uma coerção automática com os operadores + ou -:

	foo = +document.getElementById("foo-input").value;
	      ^ o operador + irá converter o operando do lado direito para um número

	// typeof foo;
	// "number"

	if ( foo === 1 ) {

		importantTask();

	}

	// `importantTask()` será chamado 
	```

	Aqui temos alguns casos comuns com coerções:


	```javascript

	// 3.B.2.1

	var number = 1,
		string = "1",
		bool = false;

	number;
	// 1

	number + "";
	// "1"

	string;
	// "1"

	+string;
	// 1

	+string++;
	// 1

	string;
	// 2

	bool;
	// false

	+bool;
	// 0

	bool + "";
	// "false"
	```


	```javascript
	// 3.B.2.2

	var number = 1,
		string = "1",
		bool = true;

	string === number;
	// false

	string === number + "";
	// true

	+string === number;
	// true

	bool === number;
	// false

	+bool === number;
	// true

	bool === string;
	// false

	bool === !!string;
	// true
	```

	```javascript
	// 3.B.2.3

	var array = [ "a", "b", "c" ];

	!!~array.indexOf( "a" );
	// true

	!!~array.indexOf( "b" );
	// true

	!!~array.indexOf( "c" );
	// true

	!!~array.indexOf( "d" );
	// false


	var num = 2.5;

	parseInt( num, 10 );

	// é o mesmo que...

	~~num;

	```

4. <a name="cond">Avaliação Condicional</a>

	```javascript

	// 4.1.1
	// Quando estiver apenas avaliando se uma array tem tamanho,
	// ao invés disso:
	if ( array.length > 0 ) ...

	// ...avalie a verdade lógica, como isso:
	if ( array.length ) ...


	// 4.1.2
	// Quando estiver apenas avaliando se uma array está vazia,
	// ao invés disso:
	if ( array.length === 0 ) ...

	// ...avalie a verdade lógica, como isso:
	if ( !array.length ) ...


	// 4.1.3
	// Quando estiver apenas avaliando se uma string não está vazia,
	// ao invés disso:
	if ( string !== "" ) ...

	// ...avalie a verdade lógica, como isso:
	if ( string ) ...


	// 4.1.4
	// Quando estiver apenas avaliando se uma string está vazia,
	// ao invés disso:
	if ( string === "" ) ...

	// ...avalie se ela é logicamente falsa, como isso:
	if ( !string ) ...


	// 4.1.5
	// Quando estiver avaliando se uma referência é verdadeira,
	// ao invés disso:
	if ( foo === true ) ...

	// ...avalie como se quisesse isso, use a vantagem de suas capacidades primitivas:
	if ( foo ) ...


	// 4.1.6
	// Quando estiver avaliando se uma referência é falsa,
	// ao invés disso:
	if ( foo === false ) ...

	// ...use a negação para coagir para uma avaliação verdadeira
	if ( !foo ) ...

	// ...Seja cuidadoso, isso também irá funcionar com: 0, "", null, undefined, NaN
	// Se você _PRECISA_ testar um valor falso de tipo booleano, então use
	if ( foo === false ) ...


	// 4.1.7
	// Quando apenas estiver avaliando uma referência que pode ser `null` ou `undefined`, mas não `false`, "" ou 0,
	// ao invés disso:
	if ( foo === null || foo === undefined ) ...

	// ...aproveite a vantagem da coerção de tipo com ==, como isso:
	if ( foo == null ) ...

	// Lembre-se, utilizando == irá funcionar em um `null` TANTO para `null` quanto para `undefined`
	// mas não para `false`, "" ou 0
	null == undefined

	```
	SEMPRE avalie para o melhor e mais preciso resultado - o que está acima é uma recomendação, não um dogma.

	```javascript

	// 4.2.1
	// Type coercion and evaluation notes

	Prefer `===` over `==` (unless the case requires loose type evaluation)

	=== does not coerce type, which means that:

	"1" === 1;
	// false

	== does coerce type, which means that:

	"1" == 1;
	// true


	// 4.2.2
	// Booleans, Truthies & Falsies

	Booleans: true, false

	Truthy are: "foo", 1

	Falsy are: "", 0, null, undefined, NaN, void 0

	```


5. <a name="practical">Practical Style</a>

	```javascript

	// 5.1.1
	// A Practical Module

	(function( global ) {
		var Module = (function() {

			var data = "secret";

			return {
				// This is some boolean property
				bool: true,
				// Some string value
				string: "a string",
				// An array property
				array: [ 1, 2, 3, 4 ],
				// An object property
				object: {
					lang: "en-Us"
				},
				getData: function() {
					// get the current value of `data`
					return data;
				},
				setData: function( value ) {
					// set the value of `data` and return it
					return ( data = value );
				}
			};
		})();

		// Other things might happen here

		// expose our module to the global object
		global.Module = Module;

	})( this );

	```

	```javascript

	// 5.2.1
	// A Practical Constructor

	(function( global ) {

		function Ctor( foo ) {

			this.foo = foo;

			return this;
		}

		Ctor.prototype.getFoo = function() {
			return this.foo;
		};

		Ctor.prototype.setFoo = function( val ) {
			return ( this.foo = val );
		};


		// To call constructor's without `new`, you might do this:
		var ctor = function( foo ) {
			return new Ctor( foo );
		};


		// expose our constructor to the global object
		global.ctor = ctor;

	})( this );

	```



6. <a name="naming">Naming</a>


	You are not a human code compiler/compressor, so don't try to be one.

	The following code is an example of egregious naming:

	```javascript

	// 6.1.1
	// Example of code with poor names

	function q(s) {
		return document.querySelectorAll(s);
	}
	var i,a=[],els=q("#foo");
	for(i=0;i<els.length;i++){a.push(els[i]);}
	```

	Without a doubt, you've written code like this - hopefully that ends today.

	Here's the same piece of logic, but with kinder, more thoughtful naming (and a readable structure):

	```javascript

	// 6.2.1
	// Example of code with improved names

	function query( selector ) {
		return document.querySelectorAll( selector );
	}

	var idx = 0,
		elements = [],
		matches = query("#foo"),
		length = matches.length;

	for( ; idx < length; idx++ ){
		elements.push( matches[ idx ] );
	}

	```

	A few additional naming pointers:

	```javascript

	// 6.3.1
	// Naming strings

	`dog` is a string


	// 6.3.2
	// Naming arrays

	`dogs` is an array of `dog` strings


	// 6.3.3
	// Naming functions, objects, instances, etc

	camelCase; function and var declarations


	// 6.3.4
	// Naming constructors, prototypes, etc.

	PascalCase; constructor function


	// 6.3.5
	// Naming regular expressions

	rDesc = //;


	// 6.3.6
	// From the Google Closure Library Style Guide

	functionNamesLikeThis;
	variableNamesLikeThis;
	ConstructorNamesLikeThis;
	EnumNamesLikeThis;
	methodNamesLikeThis;
	SYMBOLIC_CONSTANTS_LIKE_THIS;



	```

7. <a name="misc">Misc</a>

	This section will serve to illustrate ideas and concepts that should not be considered dogma, but instead exists to encourage questioning practices in an attempt to find better ways to do common JavaScript programming tasks.

	A. Using `switch` should be avoided, modern method tracing will blacklist functions with switch statements

	There seems to be drastic improvements to the execution of `switch` statements in latest releases of Firefox and Chrome.
	http://jsperf.com/switch-vs-object-literal-vs-module

	Notable improvements can be witnesses here as well:
	https://github.com/rwldrn/idiomatic.js/issues/13

	```javascript

	// 7.A.1.1
	// An example switch statement

	switch( foo ) {
		case "alpha":
			alpha();
			break;
		case "beta":
			beta();
			break;
		default:
			// something to default to
			break;
	}

	// 7.A.1.2
	// A better approach would be to use an object literal or even a module:

	var switchObj = {
		alpha: function() {
			// instruções
			// a return
		},
		beta: function() {
			// instruções
			// a return
		},
		_default: function() {
			// instruções
			// a return
		}
	};

	var switchModule = (function () {
		return {
			alpha: function() {
				// instruções
				// a return
			},
			beta: function() {
				// instruções
				// a return
			},
			_default: function() {
				// instruções
				// a return
			}
		};
	})();


	// 7.A.1.3
	// If `foo` is a property of `switchObj` or `switchModule`, execute as a method...

	( Object.hasOwnProperty.call( switchObj, foo ) && switchObj[ foo ] || switchObj._default )( args );

	( Object.hasOwnProperty.call( switchObj, foo ) && switchModule[ foo ] || switchModule._default )( args );

	// If you know and trust the value of `foo`, you could even omit the OR check
	// leaving only the execution:

	switchObj[ foo ]( args );

	switchModule[ foo ]( args );


	// This pattern also promotes code reusability.

	```

	B. Early returns promote code readability with negligible performance difference

	```javascript

	// 7.B.1.1
	// Ruim:
	function returnLate( foo ) {
		var ret;

		if ( foo ) {
			ret = "foo";
		} else {
			ret = "quux";
		}
		return ret;
	}

	// Bom:

	function returnEarly( foo ) {

		if ( foo ) {
			return "foo";
		}
		return "quux";
	}

	```


8. <a name="native">Objetos Nativos e Hospedados</a>

	O principio básico aqui é:

	### Não faça coisas estúpidas e tudo vai ficar bem.

	Para reforçar esse conceito, por favor, assista essa apresentação:

	#### “Everything is Permitted: Extending Built-ins” por Andrew Dupont (JSConf2011, Portland, Oregon)

	<iframe src="http://blip.tv/play/g_Mngr6LegI.html" width="480" height="346" frameborder="0" allowfullscreen></iframe><embed type="application/x-shockwave-flash" src="http://a.blip.tv/api.swf#g_Mngr6LegI" style="display:none"></embed>

	http://blip.tv/jsconf/jsconf2011-andrew-dupont-everything-is-permitted-extending-built-ins-5211542


9. <a name="comments">Comentários</a>

	* O estilo do JSDoc é bom (dicas de escrita do Closure Compiler++)
	* Uma linha única acima do código que é comentado
	* Multiplas linhas é boms
	* Comentários ao final da linha são proibidos!



## Apêndice

### Vírgula inicial.

Qualquer projeto que cite este documento como seu guia base de estilo não aceitará formatação de código com vírgula inicial, a não ser que isso seja explicitamente especificado de outra forma.

Veja: https://mail.mozilla.org/pipermail/es-discuss/2011-September/016805.html
Destaques: "Isso é horrível, e um motivo para rejeitar vírgulas na frente.", "vírgulas na frente devem ser evitadas"
