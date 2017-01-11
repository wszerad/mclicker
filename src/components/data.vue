<script type="text/babel">
	class Item {
		constructor(options) {
			this.title = options.title;
			this.text = options.text;
			this.type = options.type;
			this.cost = options.cost;
			this.realCost = options.realCost;
			this.position = options.position;
			this.dependencies = options.dependencies || [];
			this.performance = options.performance;
			this.active = false;
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
		}
	}

	class Upgrade extends Item {
		constructor(options) {
			options.type = 'boost';
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
			text: '',
			cost: '15k / 6 miesięcy',
			performance: 20,
			realCost: 2500
		}),
		new Dev({
			title: 'Fifeł',
			text: '',
			cost: 'Pryncypałki / 6 miesięcy',
			performance: 20,
			realCost: 2500.16
		}),
		new Dev({
			title: 'Karyna',
			text: '',
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
			text: '',
			cost: '10t koksu',
			performance: 50,
			realCost: 5000
		}),
		new Dev({
			title: 'Kacper',
			text: '',
			cost: '15k / miesiąc',
			performance: 0,
			realCost: 15000
		}),
		new Dev({
			title: 'Super Seba',
			text: '',
			cost: 'Tyle co opel pali na 100',
			performance: 999,
			realCost: 7500
		})
	];

	const boosts = [
		new Boost({
			title: 'Herbatka',
			text: '',
			cost: '2zł',
			performance: 10,
			realCost: 2
		}),
		new Boost({
			title: 'Kawa',
			text: '',
			cost: '5',
			performance: 10,
			realCost: 5
		}),
		new Boost({
			title: 'Kawa z wulkanu',
			text: '',
			cost: '20 muszelek',
			performance: 0,
			realCost: 20
		}),
		new Boost({
			title: 'Energetyk',
			text: 'Skoro jest wyprzedaż to wezme zgrzewkę, starczy na dłużej',
			cost: '1,89 w carrefour',
			performance: 20,
			realCost: 80
		}),
		new Boost({
			title: 'Chinol',
			text: 'Małe gang-bang do komara',
			cost: '1,89 w carrefour',
			performance: 99,
			realCost: 80
		}),
		new Boost({
			title: 'Nakurwach Forte',
			text: '',
			cost: '2',
			performance: 999,
			realCost: 100
		})
	];

	const upgrades = [];

	export default {
		devs,
		boosts,
		upgrades
	}
</script>