<script lang="ts">
	interface Category {
		id: number;
		name: string;
	}

	let kysymys: string[] = [];
	let pisteet: number = 0;
	let kysymysIndex: number = 0;

	async function kategoriaFetch(): Promise<Category[]> {
		const response = await fetch('https://opentdb.com/api_category.php');
		const data = await response.json();
		return data.trivia_categories;
	}
	async function kysymysFetch(kategoriaId: number) {
		const response = await fetch(
			`https://opentdb.com/api.php?amount=10&category=${kategoriaId}&difficulty=medium&type=multiple`
		);
		const data = await response.json();
		kysymys = data.results;
		kysymysIndex = 0;
		pisteet = 0;
	}

	//https://opentdb.com/api.php?amount=10&category=9&difficulty=medium&type=multiple
</script>
