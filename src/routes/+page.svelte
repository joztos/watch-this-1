async function search() {
	if (loading) return;
	searchResponse = '';
	loading = true;

	let fullSearchCriteria = `Give me a list of 5 ${cinemaType} recommendations ${
		selectedCategories ? `that fit all of the following categories: ${selectedCategories}` : ''
	}. ${
		specificDescriptors
			? `Make sure it fits the following description as well: ${specificDescriptors}.`
			: ''
	} ${
		selectedCategories || specificDescriptors
			? `If you do not have 5 recommendations that fit these criteria perfectly, do your best to suggest other ${cinemaType}'s that I might like.`
			: ''
	} Please return this response as a numbered list with the ${cinemaType}'s title, followed by a colon, and then a brief description of the ${cinemaType}. There should be a line of whitespace between each item in the list.`;

	searchResponse = await fetch('/api/search', {
		method: 'POST',
		body: JSON.stringify({ searched: fullSearchCriteria }),
		headers: {
			'content-type': 'application/json'
		}
	}).then(response => response.text());

	loading = false;
}
