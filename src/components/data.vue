<script type="text/babel">
	import engine from '../services/engine.vue';

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
			cost: '2zł',
			performance: 10,
			realCost: 2,
			time: 5
		}),
		new Boost({
			title: 'Kawa',
			text: 'Kiedy starasz się nie robić nic to się nie obejdzie',
			cost: 'Idzie wyżulić, trzeba dokupić mleko',
			performance: 10,
			realCost: 4,
			time: 90
		}),
		new Boost({
			title: 'Kawa z wulkanu',
			text: 'Zaparzanie tylko dla odważnych',
			cost: '20 muszelek',
			performance: 0,
			realCost: 20,
			time: 90
		}),
		new Boost({
			title: 'Energetyk',
			text: 'Skoro jest wyprzedaż to wezme zgrzewkę, starczy na dłużej',
			cost: '1,89zł w carrefour',
			performance: 20,
			realCost: 80,
			time: 3600
		}),
		new Boost({
			title: 'Kwadrat pizza',
			text: 'Zamówiłeś raz, więcej nie zamówisz XD',
			cost: '19zł',
			performance: 20,
			realCost: 80,
			time: 3600
		}),
		new Boost({
			title: 'Chinol',
			text: 'Małe gang-bang + ostry sos do komara',
			cost: '14,60zł',
			performance: 99,
			realCost: 80,
			time: 360
		}),
		new Boost({
			title: 'Nakurwach Forte',
			text: 'Działa krótko ale to jedyna szansa żeby wygrać 10 - 0',
			cost: 'To tajne',
			performance: 9999,
			realCost: 100,
			time: 30
		})
	];

	const upgrades = [
		new Upgrade({
			title: 'Git Shell',
			text: '',
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
			title: 'Webstorm',
			text: 'Teraz możesz się śmiać z frajerów',
			cost: 'Edukacyjna jest dla biedaków',
			realCost: 0,
			performance: 105
		}),
		new Upgrade({
			title: 'Telewizor',
			text: 'Brakuje już tylko PSa',
			cost: 'Więcej niż to warte',
			realCost: 0,
			performance: 105
		}),
		new Upgrade({
			title: 'Ekspress',
			text: '',
			cost: 'Chyba pare milionów bo nie dało się kupić',
			realCost: 0,
			performance: 105
		}),
		new Upgrade({
			title: 'Kuchnia',
			text: '',
			cost: 'więcej niż to warte',
			realCost: 0,
			performance: 105
		}),
		new Upgrade({
			title: 'BMW',
			text: '',
			cost: 'Ważne że nowa kosztuje 400k',
			realCost: 0,
			performance: 105
		}),
		new Upgrade({
			title: 'Piłkarzyki',
			text: '',
			cost: 'Warte każde pieniądze',
			realCost: 0,
			performance: 105
		}),
		new Upgrade({
			title: 'COMARCH',
			text: '',
			cost: 'więcej niż to warte',
			realCost: 0,
			performance: 105
		})
	];

	function random(chance) {
		return Math.random() < (chance / 100);
	}

	export default {
		devs,
		boosts,
		upgrades
	}
</script>