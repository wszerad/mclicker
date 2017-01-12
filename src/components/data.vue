<script type="text/babel">
	import engine from '../services/engine.vue';
	import events from '../services/events.vue';

	class Item {
		constructor(options) {
			this.title = options.title;
			this.text = options.text;
			this.type = options.type;
			this.cost = options.cost;
			this.realCost = options.realCost;
			this.dependencies = options.dependencies || [];
			this.performance = options.performance;
			this.active = false;
			this.disabled = false;
			this.event = options.event;
		}
	}

	class Dev extends Item {
		constructor(options) {
			options.type = 'dev';
			super(options);
		}
	}

	class Boost extends Item {
		constructor(options) {
			options.type = 'boost';
			super(options);

			this.time = options.time;
		}
	}

	class Upgrade extends Item {
		constructor(options) {
			options.type = 'upgrade';
			super(options);


		}
	}

	const devs = [
		new Dev({
			title: 'Mamil',
			text: 'Za 2zł zrobi wszystko, walka ze szpilą to jego chleb powszechny',
			cost: '2zł / dzień',
			performance: 10,
			realCost: 60
		}),
		new Dev({
			title: 'Dolan',
			text: 'Niedoceniony specjalista branży porno, niestety w okolicach Wieliczki nic nie kręcą',
			cost: '15k / 6 miesięcy',
			performance: 20,
			realCost: 2500
		}),
		new Dev({
			title: 'Fifeł',
			text: 'Podobno z pod łóżka można go wywabić jedynie Pryncypałkami',
			cost: 'Pryncypałki / 2 godziny',
			performance: 20,
			realCost: 2500.16
		}),
		new Dev({
			title: 'Karyna',
			text: 'Królowa przypau, dobry ziomeczek i zagorzały miesozerca',
			cost: 'Tyle co fotograf na ślubie ale na miesiąc',
			performance: 30,
			realCost: 4000
		}),
		new Dev({
			title: 'Wszeradeł',
			text: '',
			cost: '969€ / miesiąc',
			performance: 40,
			realCost: 4360
		}),
		new Dev({
			title: 'Pawcio',
			text: 'Lubi robić rzeczy na darmo i nawet nie narzeka, po zamknięciu projektu z nudów się rozchorował',
			cost: '10t koksu',
			performance: 50,
			realCost: 5000
		}),
		new Dev({
			title: 'Kacper',
			text: 'Podobno to kosmita zabłąkany w czasoprzestrzeni, to by tłumaczyło przyciasne spodnie i rekurencyjne $timeouty',
			cost: '15k / miesiąc',
			performance: 0,
			realCost: 15000
		}),
		new Dev({
			title: 'Super Seba',
			text: 'Nawet jeśli wiesz lepiej to nie wiesz lepiej, wirtuoz wśród programistów (bo po szkole muzycznej)',
			cost: 'Tyle co opel pali na 100',
			performance: 999,
			realCost: 7500
		})
	];

	const boosts = [
		new Boost({
			title: 'Herbatka',
			text: 'Nawet nie zaczynaj dnia bez rozpoczęcia tym specyfikiem',
			cost: 'Jak komuś zwędzisz to nawet nie zauważy',
			performance: 10,
			realCost: 2,
			time: 5
		}),
		new Boost({
			title: 'Kawa',
			text: 'Kiedy starasz się nie robić nic to się nie obejdzie',
			cost: 'Idzie wyżulić, trzeba dokupić mleko',
			performance: 15,
			realCost: 4,
			time: 7
		}),
		new Boost({
			title: 'Kawa z wulkanu',
			text: 'Zaparzanie tylko dla odważnych',
			cost: '20 muszelek',
			performance: 12,
			realCost: 20,
			time: 6,
			event() {
				if(isActive('Ekspress') && random(50)) {
					getItem('Ekspress').active = false;
					return 'Rozdupcyło ekspress';
				}
			}
		}),
		new Boost({
			title: 'Kwadrat pizza',
			text: 'Zamówiłeś raz, więcej nie zamówisz XD',
			cost: '19zł',
			performance: 1,
			realCost: 80,
			time: 360,
			event() {
				this.dependencies = ['Chyba cie pojebało...'];
				return 'Zamówiłeś raz pizze kwadrat, więcej nie zamówisz XD';
			}
		}),
		new Boost({
			title: 'Energetyk',
			text: 'Skoro jest wyprzedaż to wezme zgrzewkę, starczy na dłużej',
			cost: '1,89zł w carrefour',
			performance: 20,
			realCost: 80,
			time: 10
		}),
		new Boost({
			title: 'Chinol',
			text: 'Małe gang-bang + ostry sos do komara',
			cost: '14,60zł',
			performance: 50,
			realCost: 100,
			time: 20
		}),
		new Boost({
			title: 'Nakurwach Forte',
			text: 'Działa krótko ale to jedyna szansa żeby wygrać 10 - 0',
			cost: 'To tajne',
			performance: 100,
			realCost: 200,
			time: 5,
			event() {
				if(random(20)) {
					engine.clickable = false;
					setTimeout(function() {
						engine.clickable = true;
					}, 10000);

					return 'Przedawkowałeś Nakurwach, leżych nagi pod prysznicem';
				}
			}
		})
	];

	const upgrades = [
		new Upgrade({
			title: 'Git Shell',
			text: 'Szacunek wśród kolegów mimo że nie ogarniasz',
			cost: 'Darmowa',
			realCost: 0,
			performance: 105,
			event() {
				if(random(100)) {
					engine.clickable = false;
					setTimeout(function() {
						engine.clickable = true;
					}, 10000);

					return 'Hehe popsułeś developa, tracisz czas na naprawę developa';
				}
			}
		}),
		new Upgrade({
			title: 'Piłkarzyki',
			text: 'To tu wypływają największe głupoty :D',
			cost: 'Warte każde pieniądze',
			realCost: 200,
			performance: 120,
			event() {
				var self = this;
				engine.$on('tick', function () {
					if(!this.disabled && random(3)) {
						events.emit('Złamałeś drongala, wydajność zespołu spada');
						self.disabled = true;
						setTimeout(function() {
							self.disabled = false;
						}, 10000);
					}
				});
			}
		}),
		new Upgrade({
			title: 'Webstorm',
			text: 'Teraz możesz się śmiać z frajerów',
			cost: 'Edukacyjna jest dla biedaków',
			realCost: 400,
			performance: 150
		}),
		new Upgrade({
			title: 'Ekspress',
			text: 'Szkoda że zapach kawy nie jest w stanie przebić się przez smog',
			cost: 'Chyba pare milionów bo nie dało się kupić',
			realCost: 900,
			performance: 120,
			event() {
				var self = this;
				engine.$on('tick', function () {
					if(!this.disabled && random(3)) {
						events.emit('Znów ktoś nie umył filtra, traw przesłuchiwanie podejrzanych');
						self.disabled = true;
						setTimeout(function() {
							self.disabled = false;
						}, 8000);
					}
				});
			}
		}),
		new Upgrade({
			title: 'Telewizor',
			text: 'Brakuje już tylko PSa',
			cost: 'Taniej wychodzi w zestawie',
			realCost: 2000,
			performance: 101
		}),
		new Upgrade({
			title: 'Kuchnia',
			text: 'Tablica na facebooku się chowa, tylko tu panuje wolność słowa',
			cost: 'Nieważne, musi być',
			realCost: 10000,
			performance: 105
		}),
		new Upgrade({
			title: 'BMW',
			text: 'Można dać w pizde aż do następnych świateł',
			cost: 'Ważne że nowa kosztuje 400k',
			realCost: 40000,
			performance: 110,
			event() {
				var self = this;
				engine.$on('tick', function () {
					if(!this.disabled && random(4)) {
						events.emit('Wlazłeś w gówno! Przecież tak nie można wsiadać do samochodu');
						self.disabled = true;
						setTimeout(function() {
							self.disabled = false;
						}, 5000);
					}
				});
			}
		}),
		new Upgrade({
			title: 'COMARCH',
			text: 'Teraz już możesz zwolnić Profesora i wszystich magistrów',
			cost: 'Więcej niż to warte',
			realCost: 10000000,
			performance: 1000
		}),
		new Upgrade({
			title: 'Zwolnij Profesora',
			text: 'Teraz już możesz zwolnić Profesora i wszystich magistrów',
			cost: 'Bezcenne',
			realCost: 0,
			performance: 10000,
			dependencies: ['COMARCH']
		})
	];

	const all = [].concat(devs, boosts, upgrades);

	function getItem(name) {
		return all.find(function (item) {
			return item.title === name;
		})
	}

	function isActive(name) {
		return all.some(function (item) {
			return item.active && item.title === name;
		});
	}

	function random(chance) {
		return Math.random() < (chance / 100);
	}

	export default {
		devs,
		boosts,
		upgrades
	}
</script>