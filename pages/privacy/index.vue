<template>
	<div class='container'>
		<h1 class="h1__title">{{ pageTitle }}</h1>
		<div class="privacy">
			<div class="privacy__nav">
				<div class="privacy__link"
				     @click="activeTab = item.id" v-for="item in nav" :key="item.id">
					{{ item.name }}
				</div>
			</div>
			<component :is="`texts-privacy-${activeTab}`" class="privacy__content"/>
		</div>
	</div>
</template>
<script>
import seoTags from "@/mixins/seoTags";

export default {
	mixins: [seoTags],
	components:{
		TextsPrivacyConf:()=> import('~/components/texts/texts-privacy/texts-privacy-conf'),
		TextsPrivacyCookie:()=> import('~/components/texts/texts-privacy/texts-privacy-cookie'),
		TextsPrivacyObrabotka:()=> import('~/components/texts/texts-privacy/texts-privacy-obrabotka'),
		TextsPrivacyOtkaz:()=> import('~/components/texts/texts-privacy/texts-privacy-otkaz'),
		TextsPrivacyPersonal:()=> import('~/components/texts/texts-privacy/texts-privacy-personal'),
	},
	data() {
		return {
			activeTab: 'conf',
			nav: [
				{
					id: 'conf',
					name: 'Политика конфиденциальности'
				},
				{
					id: 'obrabotka',
					name: 'Политика в отношении обработки персональных данных'
				},
				{
					id: 'cookie',
					name: 'Файлы Cookie и анализ посещения сайта'
				},
				{
					id: 'otkaz',
					name: 'Отказ от заверений и гарантий'
				},
				{
					id: 'personal',
					name: 'Согласие на обработку персональных данных'
				}
			]
		}
	}
}
</script>
