# Joukkueen otteluseuranta — Projektidokumentaatio

**Tekijä:** Alhassan Alhakeem
**Kausi:** 2025
**Teknologia:** HTML, CSS, JavaScript

---

## Vaihe 1: Business case ja arvolupaus

### Ongelma

Harrastejalkapalloilijat seuraavat joukkueensa tuloksia usein WhatsApp-viesteistä, muistista tai hajallaan olevista taulukoista. Kauden tilastoja ei juuri koskaan koota yhteen paikkaan, jolloin esimerkiksi maalintekijätilastot tai voittoprosentti jää arvailun varaan.

### Kohderyhmä

Harrastejalkapalloa pelaavat aikuiset, jotka haluavat seurata oman joukkueensa kauden kulkua ilman ylimääräistä vaivaa.

### Arvolupaus

Tavallinen jalkapalloilija näkee yhdellä silmäyksellä joukkueensa kauden tulokset, maalintekijätilastot ja kauden yhteenvedon — ilman taulukoita tai muistiinpanoja.

---

## Vaihe 2: Käyttäjäskenaariot

### Skenaario 1 — Ottelun jälkeen

Matti pelasi juuri 3–1-voiton. Hän avaa sovelluksen puhelimellaan, siirtyy "Kirjaa ottelu" -välilehdelle ja täyttää vastustajan nimen, päivän, tuloksen ja maalintekijät. Kirjaaminen kestää alle minuutin. Sovellus tallentaa tiedot automaattisesti ja näyttää päivitetyn kausitilanteen.

### Skenaario 2 — Kauden tilanteen tarkistaminen

Kauden puolivälissä Matti haluaa tietää, kuinka monta voittoa joukkueella on ja kuka on tehnyt eniten maaleja. Hän avaa sovelluksen ja näkee kauden yhteenvedon sekä maalintekijätilaston heti etusivulla ilman hakuja tai laskemista.

### Skenaario 3 — Virheenkorjaus

Matti huomaa kirjanneensa väärän tuloksen viime viikon otteluun. Hän etsii ottelun listalta, painaa "Muokkaa" ja korjaa tuloksen. Muutos tallentuu välittömästi.

---

## Vaihe 3: Speksit ja vaatimukset

### Tavoite

Selainpohjainen sovellus harrastejalkapalloilijalle joukkueen ottelutulosten ja maalintekijätilastojen seurantaan koko kauden ajalta.

### Laajuus

Yhden joukkueen kauden seuranta. Ei kirjautumista, ei monen joukkueen hallintaa.

### Rajaukset

- Ei käyttäjätunnuksia tai kirjautumista
- Ei reaaliaikaista synkronointia muille käyttäjille
- Ei mobiilisovellusta — toimii selaimessa
- Ei ulkoisia kirjastoja tai tietokantoja

### Toiminnalliset vaatimukset

1. Käyttäjä voi lisätä ottelun (vastustaja, päivä, tulos, maalintekijät)
2. Käyttäjä voi muokata tallennettua ottelua
3. Käyttäjä voi poistaa ottelun
4. Käyttäjä näkee listan kaikista otteluista uusimmasta vanhimpaan
5. Käyttäjä näkee kauden yhteenvedon (voitot, tasapelit, häviöt, maaliero, ottelumäärä)
6. Käyttäjä näkee maalintekijätilastot järjestettynä maalimäärän mukaan

### Ei-toiminnalliset vaatimukset

- Sovellus toimii selaimessa ilman asennusta
- Käyttöliittymä toimii mobiilissa
- Tiedot tallennetaan selaimen local storageen
- Sovellus näyttää virheilmoituksen jos lomake on puutteellinen

### Riskit ja oletukset

- Data häviää jos selaimen local storage tyhjennetään
- Sovellusta käyttää vain yksi henkilö kerrallaan

---

## Vaihe 4: Alkuprompt

Alla on alkuprompt, jota käytettiin AI-työkalun ohjaamiseen projektin toteutusvaiheessa.

---

**Konteksti:** Rakennan selainpohjaisen web-sovelluksen harrastejalkapalloilijalle. Sovelluksen avulla pelaaja voi seurata joukkueensa ottelutuloksia ja maalintekijätilastoja koko kauden ajalta.

**Käyttäjä:** Tavallinen harrastepelaaja, ei teknistä osaamista. Käyttää sovellusta puhelimella tai tietokoneella ottelun jälkeen.

**Toteuta seuraavat toiminnot:**
1. Ottelun lisääminen: vastustaja, päivä, oma tulos, vastustajan tulos, maalintekijät (pelaajan nimi + maalimäärä)
2. Otteluiden listaus ja muokkaus/poisto
3. Kauden yhteenveto: voitot, tasapelit, häviöt, maaliero
4. Maalintekijätilasto järjestettynä maalimäärän mukaan

**Rajaukset:** Ei kirjautumista. Tiedot tallennetaan local storageen. Ei ulkoisia kirjastoja tai tietokantoja — pelkkä HTML, CSS ja JavaScript yhdessä tiedostossa.

**Lopputulos:** Yksi toimiva HTML-tiedosto, jota voi avata suoraan selaimessa.

---

## Vaihe 5: Toteutus

Sovellus on toteutettu yhtenä HTML-tiedostona (`index.html`), joka sisältää kaiken HTML-, CSS- ja JavaScript-koodin.

### Rakenne

- **Kausi-välilehti** — kauden yhteenveto (voitot, tasapelit, häviöt, maaliero) ja ottelulista
- **Kirjaa ottelu -välilehti** — lomake uuden ottelun lisäämiseen ja vanhan muokkaamiseen
- **Tilastot-välilehti** — maalintekijät järjestettynä maalimäärän mukaan

### Tekninen toteutus

- Kieli: HTML5, CSS3, JavaScript (ES6)
- Tallennus: selaimen localStorage
- Ei ulkoisia riippuvuuksia
- Toimii kaikissa moderneissa selaimissa

### Repo

GitHub: https://github.com/Alhassan-Alhakeem/jalkapallo-seuranta

Live: https://alhassan-alhakeem.github.io/jalkapallo-seuranta

---

## Vaihe 6: Testaus

### Toiminnalliset testit

#### T1 — Ottelun lisääminen

**Vaatimus:** Käyttäjä voi lisätä ottelun

| Askel | Toiminto | Odotettu tulos | Tulos |
|-------|----------|----------------|-------|
| 1 | Avaa "Kirjaa ottelu" -välilehti | Lomake aukeaa | ✅ |
| 2 | Syötä vastustaja, päivä, tulos | Kentät täyttyvät | ✅ |
| 3 | Lisää maalintekijä napilla | Uusi rivi ilmestyy | ✅ |
| 4 | Paina "Tallenna" | Ottelu tallentuu, siirtyy Kausi-näkymään | ✅ |

#### T2 — Ottelun muokkaaminen

**Vaatimus:** Käyttäjä voi muokata tallennettua ottelua

| Askel | Toiminto | Odotettu tulos | Tulos |
|-------|----------|----------------|-------|
| 1 | Paina "Muokkaa" ottelun kohdalla | Lomake täyttyy vanhoilla tiedoilla | ✅ |
| 2 | Muuta tulos tai maalintekijä | Kenttä päivittyy | ✅ |
| 3 | Paina "Tallenna" | Muutos näkyy ottelulistassa | ✅ |

#### T3 — Ottelun poistaminen

**Vaatimus:** Käyttäjä voi poistaa ottelun

| Askel | Toiminto | Odotettu tulos | Tulos |
|-------|----------|----------------|-------|
| 1 | Paina "Poista" ottelun kohdalla | Ottelu häviää listalta | ✅ |
| 2 | Tarkista kauden yhteenveto | Tilastot päivittyvät | ✅ |

#### T4 — Otteluiden listaus

**Vaatimus:** Käyttäjä näkee listan kaikista otteluista

| Askel | Toiminto | Odotettu tulos | Tulos |
|-------|----------|----------------|-------|
| 1 | Avaa "Kausi"-välilehti | Lista näkyy uusimmasta vanhimpaan | ✅ |
| 2 | Tarkista värikoodaus | Voitto = vihreä, tasapeli = keltainen, häviö = punainen | ✅ |

#### T5 — Kauden yhteenveto

**Vaatimus:** Käyttäjä näkee voitot, tasapelit, häviöt ja maalieron

| Askel | Toiminto | Odotettu tulos | Tulos |
|-------|----------|----------------|-------|
| 1 | Lisää 3 ottelua: 3-1, 2-2, 0-2 | Tallennetaan | ✅ |
| 2 | Tarkista yhteenveto | V:1, T:1, H:1, Maalit: 5-5 | ✅ |

#### T6 — Maalintekijätilasto

**Vaatimus:** Käyttäjä näkee tilastot maalimäärän mukaan järjestettynä

| Askel | Toiminto | Odotettu tulos | Tulos |
|-------|----------|----------------|-------|
| 1 | Avaa "Tilastot"-välilehti | Maalintekijälista näkyy | ✅ |
| 2 | Tarkista järjestys | Eniten maaleja tehnyt on ensimmäisenä | ✅ |
| 3 | Lisää uusi maali samalle pelaajalle | Kokonaissumma päivittyy | ✅ |

### Virhetilanteiden testit

| Tilanne | Odotettu tulos | Tulos |
|---------|----------------|-------|
| Tallennetaan ilman vastustajan nimeä | Virheilmoitus: "Syötä vastustajan nimi." | ✅ |
| Tallennetaan ilman päivämäärää | Virheilmoitus: "Valitse päivämäärä." | ✅ |
| Kausi-näkymä ilman otteluita | Teksti: "Ei otteluita vielä." | ✅ |
| Tilastot ilman maalintekijöitä | Teksti: "Ei maalintekijätietoja vielä." | ✅ |

### Ei-toiminnalliset testit

| Vaatimus | Testi | Tulos |
|----------|-------|-------|
| Toimii selaimessa | Testattu Chrome, Firefox | ✅ |
| Toimii mobiilissa | Testattu mobiilikoossa (375px) | ✅ |
| Tiedot tallennetaan | Sivu päivitetty — tiedot säilyivät | ✅ |
| Virheilmoitukset näkyvät | Punainen teksti lomakkeen alla | ✅ |

### Yhteenveto

Kaikki 6 toiminnallista vaatimusta testattiin ja läpäisivät testit. Virhetilanteet käsitellään oikein. Sovellus toimii selaimessa ja mobiilissa.

---

## Vaihe 7: Validointi

### Alkuperäinen ongelma

Harrastejalkapalloilijat seuraavat joukkueensa tuloksia hajallaan — WhatsApp-viesteistä, muistista tai taulukoista. Kauden tilastoja ei koota yhteen paikkaan.

### Vastattiinko ongelmaan?

Kyllä. Sovellus tarjoaa yhden selkeän paikan, jonne käyttäjä voi kirjata ottelut ja nähdä kauden tilanteen yhdellä silmäyksellä. Maalintekijätilasto kokoaa tiedon, jota ei aiemmin ollut helposti saatavilla.

### Käyttäjätarpeiden täyttyminen

| Käyttäjäskenaario | Täyttyi? | Huomio |
|-------------------|----------|--------|
| Ottelun kirjaaminen ottelun jälkeen | ✅ Kyllä | Nopea, alle minuutin toimenpide |
| Kauden tilanteen tarkistaminen | ✅ Kyllä | Yhteenveto näkyy heti etusivulla |
| Virheellisen tuloksen korjaaminen | ✅ Kyllä | Muokkaus onnistuu suoraan listalta |

### Vaatimusten täyttyminen

| Vaatimus | Täyttyi? |
|----------|----------|
| Ottelun lisääminen | ✅ |
| Ottelun muokkaaminen | ✅ |
| Ottelun poistaminen | ✅ |
| Otteluiden listaus | ✅ |
| Kauden yhteenveto | ✅ |
| Maalintekijätilasto | ✅ |
| Toimii selaimessa | ✅ |
| Mobiiliystävällinen | ✅ |
| Virheilmoitukset | ✅ |
| Tiedot tallennetaan | ✅ |

### Missä ratkaisu jäi vajaaksi?

**Datan pysyvyys:** Tiedot tallennetaan selaimen local storageen, joten ne häviävät jos selain tyhjennetään tai vaihdetaan. Oikeassa tuotantokäytössä tarvittaisiin pilvipalvelu tai tiedostovienti.

**Yhden käyttäjän rajoitus:** Sovellus on suunniteltu yhdelle käyttäjälle. Joukkueen kaikki pelaajat eivät näe samoja tietoja ilman tietokantaa ja kirjautumista.

**Ei varmuuskopiointia:** Käyttäjällä ei ole mahdollisuutta viedä tietoja CSV-tiedostona tai jakaa niitä muille.

### Kokonaisarvio

Sovellus ratkaisee alkuperäisen ongelman hyvin demokäytössä ja henkilökohtaisessa seurannassa. Se on teknisesti toimiva, helppokäyttöinen ja vastaa kaikkiin määriteltyihin vaatimuksiin. Jatkokehityskohteina datan pysyvyys ja monen käyttäjän tuki olisivat luontevia seuraavia askelia.
