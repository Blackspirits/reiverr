<script lang="ts">
	import { addMessages, init, locale } from 'svelte-i18n';

	import de from '../../lang/de.json';
	import en from '../../lang/en.json';
	import es from '../../lang/es.json';
	import fr from '../../lang/fr.json';
	import it from '../../lang/it.json';
	import ptPT from '../../lang/pt-PT.json';
	import ptBR from '../../lang/pt-BR.json';
	import { settings } from '../../stores/settings.store';

	addMessages('de', de);
	addMessages('en', en);
	addMessages('es', es);
	addMessages('fr', fr);
	addMessages('it', it);
	addMessages('pt_PT', ptPT);
	addMessages('pt_BR', ptBR);

	settings.subscribe((value) => {
		if (value.language) {
			locale.set(value.language);
		} else {
			locale.set('en');
		}
	});

	init({
		initialLocale: $settings.language,
		fallbackLocale: 'en'
	});
</script>
