# Prototype

**Prototype** - спеціальний ключ в обєктах js за допомогою якого організовуються ланцюги обєктів так, щоб властивість яку 
не знайдено в одному обєкті шукалась в іншому, посилання на обєкт прототип міститься в ключу __proto__ обєкта.

***

	function Animal(name) {
		this.name = name;
		this.canWalk = true;
	}

	Animal.prototype = {
		constructor: Animal,
		run: function() {
			console.log('run - ' + this.name);
		}
	}

	function Rabbit(name) {
		Animal.apply(this, arguments);
		this.speed = 0;
	}
 
	Rabbit.prototype = Object.create(Animal.prototype);
	Rabbit.prototype.constructor = Rabbit;

	Rabbit.prototype.jump = function() {
		this.speed++;
		alert( this.name + ' прыгает' );
	};

***

	class Animal {
	  constructor(name) {
	    this.name = name;
	  }

	  run() {
	    console.log(`run ${this.name}`);
	  }
	}

	class Rabbit extends Animal {
	  constructor(name) {
	    super(name);
	    this.canJump = true;
	  }

	  jump() {
	    console.log('jump' + this.name);
	  }
	}

	console.log(Animal);
	console.log(Rabbit);

	let cow = new Animal('cow');
	console.log(cow);

	let banni = new Rabbit('banni');
	console.log(banni);
