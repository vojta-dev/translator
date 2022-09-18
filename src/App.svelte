<script>
  import { WORDS } from './words';

  // prettier-ignore
  const LANGUAGES = ['Afrikaans','Albanian','Amharic','Arabic','Armenian','Assamese','Aymara','Azerbaijani','Bambara','Basque','Belarusian','Bengali','Bhojpuri','Bosnian','Bulgarian','Catalan','Cebuano','Chichewa','Chinese(Simplified)','Chinese(Traditional)','Corsican','Croatian','history','Czech','Danish','Dhivehi','Dogri','Dutch','check','English','Esperanto','Estonian','Ewe','Filipino','Finnish','French','Frisian','Galician','Georgian','German','Greek','Guarani','Gujarati','HaitianCreole','Hausa','Hawaiian','Hebrew','Hindi','Hmong','Hungarian','Icelandic','Igbo','Ilocano','Indonesian','Irish','Italian','Japanese','Javanese','Kannada','Kazakh','Khmer','Kinyarwanda','Konkani','Korean','Krio','Kurdish(Kurmanji)','Kurdish(Sorani)','Kyrgyz','Lao','Latin','Latvian','Lingala','Lithuanian','Luganda','Luxembourgish','Macedonian','Maithili','Malagasy','Malay','Malayalam','Maltese','Maori','Marathi','Meiteilon(Manipuri)','Mizo','Mongolian','Myanmar(Burmese)','Nepali','Norwegian','Odia(Oriya)','Oromo','Pashto','Persian','Polish','Portuguese','Punjabi','Quechua','Romanian','Russian','Samoan','Sanskrit','ScotsGaelic','Sepedi','Serbian','Sesotho','Shona','Sindhi','Sinhala','Slovak','Slovenian','Somali','history','Spanish','Sundanese','Swahili','Swedish','Tajik','Tamil','Tatar','Telugu','Thai','Tigrinya','Tsonga','Turkish','Turkmen','Twi','Ukrainian','Urdu','Uyghur','Uzbek','Vietnamese','Welsh','Xhosa','Yiddish','Yoruba','Zulu']

  let input = '';
  let translation = 'Your translation will appear here';

  function handleClick() {
    translation = '';
    for (let i = 0; i < input.trim().split(/\s+/g).length; i++) {
      translation += getRandomWord() + ' ';
    }
  }

  function getRandomWord() {
    return WORDS[Math.floor(Math.random() * WORDS.length)];
  }
</script>

<h1>Translator</h1>

<main>
  <div>
    From
    <select>
      {#each LANGUAGES as language}
        <option>{language}</option>
      {/each}
    </select>
    to English
  </div>

  <div>
    <textarea cols="40" rows="5" bind:value={input} />
  </div>

  <button on:click={handleClick}>TRANSLATE</button>

  <div class="translation">{translation}</div>
</main>

<footer>
  <small>
    &copy; {new Date().getFullYear()} Vojta | <a href="https://github.com/vojta-dev/translator">GitHub</a>
  </small>
</footer>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Quicksand:wght@400;700&display=swap');

  :global(body) {
    margin: 0;
    background-color: #282c34;
    color: white;
    font-family: 'Quicksand';
  }

  h1 {
    text-align: center;
    font-family: 'Quicksand', sans-serif;
    font-size: 5rem;
    line-height: 5rem;
  }

  main {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 2rem;
    font-size: 1.5rem;
  }
  main * {
    font-size: inherit;
  }

  select {
    padding: 0.5rem;
    border-radius: 8px;
  }

  textarea {
    font-family: --apple-sysetm, system-ui, sans-serif;
    padding: 0.5rem;
    border-radius: 8px;
  }

  button {
    padding: 1rem;
    background: none;
    color: inherit;
    border: 2px solid aqua;
    border-radius: 8px;
    transition: background-color 100ms;
    cursor: pointer;
  }
  button:hover {
    background-color: aqua;
    color: #282c34;
  }

  .translation {
    background-color: white;
    min-width: 20rem;
    max-width: 80vw;
    min-height: 5rem;
    border-radius: 8px;
    color: #282c34;
    padding: 1rem;
  }

  footer {
    position: absolute;
    bottom: 1rem;
    width: 100%;
    text-align: center;
  }

  footer a {
    color: #60a5fa;
    text-decoration: none;
  }
</style>
