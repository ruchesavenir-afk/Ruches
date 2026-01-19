{
  "site": {
    "nom": "Les ruches de l'avenir",
    "description": "Apiculteur local à Villevêque et Cheffes. Production de miel non chauffé et élevage d’essaims sélectionnés.",
    "telephone": "06 52 20 89 98",
    "email": "Ruches.avenir@gmail.com",
    "localisation": "Villevêque et Cheffes (Maine-et-Loire)"
  },

  "presentation": {
    "titre": "Une apiculture durable et passionnée",
    "texte": "Passionné d’apiculture depuis plus de 10 ans, je produis un miel local, non chauffé, sans transhumance. Mes pratiques respectent le cycle naturel des abeilles et visent à préserver la biodiversité."
  },

  "miels": [
    {
      "nom": "Miel de printemps",
      "description": "Miel doux et floral issu des premières floraisons locales.",
      "imageMiel": "images/miel-printemps.jpg",
      "imageFleur": "images/fleur-printemps.jpg"
    },
    {
      "nom": "Miel d’acacia",
      "description": "Miel clair, délicat et apprécié pour sa finesse.",
      "imageMiel": "images/miel-acacia.jpg",
      "imageFleur": "images/fleur-acacia.jpg"
    },
    {
      "nom": "Miel de fleurs sauvages",
      "description": "Miel de caractère issu d’une grande diversité florale.",
      "imageMiel": "images/miel-fleurs.jpg",
      "imageFleur": "images/fleur-sauvage.jpg"
    }
  ],

  "elevage": {
    "texte": "Vente d’essaims hivernés et de l’année issus de colonies sélectionnées sur la production de miel, la douceur et la lenteur à essaimer. Critères secondaires : hygiénisme, gestion du varroa, consommation hivernale et réserves.",
    "prix": "Prix dégressifs selon quantité, me contacter."
  }
}
<script>
fetch("content.json")
.then(res => res.json())
.then(data => {

  document.querySelectorAll("[data-site-nom]")
    .forEach(el => el.textContent = data.site.nom);

  document.querySelector("[data-presentation-titre]").textContent =
    data.presentation.titre;

  document.querySelector("[data-presentation-texte]").textContent =
    data.presentation.texte;

  // Miels
  const container = document.querySelector("[data-miels]");
  if (container) {
    data.miels.forEach(miel => {
      container.innerHTML += `
        <article class="card">
          <img src="${miel.imageMiel}" alt="${miel.nom}">
          <img src="${miel.imageFleur}" alt="Fleur ${miel.nom}">
          <h3>${miel.nom}</h3>
          <p>${miel.description}</p>
        </article>`;
    });
  }

  // Contact
  if (document.querySelector("[data-telephone]")) {
    document.querySelector("[data-telephone]").textContent = data.site.telephone;
    document.querySelector("[data-email]").textContent = data.site.email;
  }
});
</script>
<!DOCTYPE html>
<html lang="fr">
<head>
<title>Les ruches de l'avenir – Apiculteur à Villevêque</title>
<meta name="description" content="Apiculteur local à Villevêque et Cheffes. Miel non chauffé, sans transhumance et élevage d’essaims sélectionnés.">
<meta name="robots" content="index, follow">
<link rel="stylesheet" href="style.css">

<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "Les ruches de l'avenir",
  "description": "Apiculture locale, miel non chauffé",
  "areaServed": "Maine-et-Loire",
  "telephone": "0652208998",
  "email": "Ruches.avenir@gmail.com"
}
</script>
</head>

<body>
<header>
<h1 data-site-nom></h1>
<nav>
<a href="miel.html">Miel</a>
<a href="elevage.html">Élevage</a>
<a href="contact.html">Contact</a>
</nav>
</header>

<section>
<h2 data-presentation-titre></h2>
<p data-presentation-texte></p>
</section>

<script src="script.js"></script>
</body>
</html>
<h1>Miels artisanaux locaux</h1>
<section data-miels class="grid"></section>
<h1>Contact apiculteur</h1>
<p>Téléphone : <span data-telephone></span></p>
<p>Email : <span data-email></span></p>
