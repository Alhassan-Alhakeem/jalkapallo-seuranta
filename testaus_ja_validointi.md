# Joukkueen otteluseuranta – Testaus ja validointi

---

## Vaihe 6: Testaus

### Testauksen tavoite

Testauksen tarkoitus on varmistaa, että sovellus toimii määriteltyjen toiminnallisten ja ei-toiminnallisten vaatimusten mukaisesti.

---

### Toiminnalliset testit

#### T1 – Ottelun lisääminen

**Vaatimus:** Käyttäjä voi lisätä ottelun (vastustaja, päivä, tulos, maalintekijät)

| Askel | Toiminto | Odotettu tulos | Tulos |
|-------|----------|----------------|-------|
| 1 | Avaa "Kirjaa ottelu" -välilehti | Lomake aukeaa | ✅ |
| 2 | Syötä vastustaja, päivä, tulos | Kentät täyttyvät | ✅ |
| 3 | Lisää maalintekijä napilla | Uusi rivi ilmestyy | ✅ |
| 4 | Paina "Tallenna" | Ottelu tallentuu ja siirtyy Kausi-näkymään | ✅ |

---

#### T2 – Ottelun muokkaaminen

**Vaatimus:** Käyttäjä voi muokata tallennettua ottelua

| Askel | Toiminto | Odotettu tulos | Tulos |
|-------|----------|----------------|-------|
| 1 | Paina "Muokkaa" ottelun kohdalla | Lomake täyttyy vanhoilla tiedoilla | ✅ |
| 2 | Muuta tulos tai maalintekijä | Kenttä päivittyy | ✅ |
| 3 | Paina "Tallenna" | Muutos näkyy ottelulistassa | ✅ |

---

#### T3 – Ottelun poistaminen

**Vaatimus:** Käyttäjä voi poistaa ottelun

| Askel | Toiminto | Odotettu tulos | Tulos |
|-------|----------|----------------|-------|
| 1 | Paina "Poista" ottelun kohdalla | Ottelu häviää listalta | ✅ |
| 2 | Tarkista kauden yhteenveto | Tilastot päivittyvät | ✅ |

---

#### T4 – Otteluiden listaus

**Vaatimus:** Käyttäjä näkee listan kaikista otteluista

| Askel | Toiminto | Odotettu tulos | Tulos |
|-------|----------|----------------|-------|
| 1 | Avaa "Kausi"-välilehti | Lista näkyy uusimmasta vanhimpaan | ✅ |
| 2 | Tarkista värikoodaus | Voitto = vihreä, tasapeli = keltainen, häviö = punainen | ✅ |

---

#### T5 – Kauden yhteenveto

**Vaatimus:** Käyttäjä näkee voitot, tasapelit, häviöt ja maalieron

| Askel | Toiminto | Odotettu tulos | Tulos |
|-------|----------|----------------|-------|
| 1 | Lisää 3 ottelua: voitto 3-1, tasapeli 2-2, häviö 0-2 | Tallennetaan | ✅ |
| 2 | Tarkista yhteenveto | V:1, T:1, H:1, Maalit: 5-5 | ✅ |

---

#### T6 – Maalintekijätilasto

**Vaatimus:** Käyttäjä näkee tilastot maalimäärän mukaan järjestettynä

| Askel | Toiminto | Odotettu tulos | Tulos |
|-------|----------|----------------|-------|
| 1 | Avaa "Tilastot"-välilehti | Maalintekijälista näkyy | ✅ |
| 2 | Tarkista järjestys | Eniten maaleja tehnyt on ensimmäisenä | ✅ |
| 3 | Tee uusi maalinkirjaus samalle pelaajalle | Kokonaissumma päivittyy | ✅ |

---

### Virhetilanteiden testit

#### V1 – Tyhjä lomake

| Tilanne | Odotettu tulos | Tulos |
|---------|----------------|-------|
| Tallennetaan ilman vastustajan nimeä | Virheilmoitus: "Syötä vastustajan nimi." | ✅ |
| Tallennetaan ilman päivämäärää | Virheilmoitus: "Valitse päivämäärä." | ✅ |

#### V2 – Ei otteluita

| Tilanne | Odotettu tulos | Tulos |
|---------|----------------|-------|
| Kausi-näkymä ilman otteluita | Teksti: "Ei otteluita vielä." | ✅ |
| Tilastot ilman maalintekijöitä | Teksti: "Ei maalintekijätietoja vielä." | ✅ |

---

### Ei-toiminnalliset testit

| Vaatimus | Testi | Tulos |
|----------|-------|-------|
| Toimii selaimessa | Avattiin Chrome, Firefox, Safari | ✅ |
| Toimii mobiilissa | Testattu mobiilikoossa (375px leveys) | ✅ |
| Tiedot tallentuvat | Sivu päivitetty – tiedot säilyivät | ✅ |
| Virheilmoitukset näkyvät selkeästi | Punainen teksti lomakkeen alla | ✅ |

---

### Yhteenveto testauksesta

Kaikki 6 toiminnallista vaatimusta testattiin ja läpäisivät testit. Virhetilanteet käsitellään oikein. Sovellus toimii selaimessa ja mobiilissa ilman ongelmia.

---

## Vaihe 7: Validointi

### Validoinnin tavoite

Validoinnissa arvioidaan, ratkaisiko toteutus alkuperäisen ongelman ja tukeeko se käyttäjän todellisia tarpeita.

---

### Alkuperäinen ongelma

Harrastejalkapalloilijat seuraavat joukkueensa tuloksia hajallaan – WhatsApp-viesteistä, muistista tai taulukoista. Kauden tilastoja ei koota yhteen paikkaan.

### Vastattiinko ongelmaan?

**Kyllä.** Sovellus tarjoaa yhden selkeän paikan, jonne käyttäjä voi kirjata ottelut ja nähdä kauden tilanteen yhdellä silmäyksellä. Maalintekijätilasto kokoaa tiedon, jota ei aiemmin ollut helposti saatavilla.

---

### Käyttäjätarpeiden täyttyminen

| Käyttäjäskenaario | Täyttyikö? | Huomio |
|-------------------|------------|--------|
| Ottelun kirjaaminen ottelun jälkeen | ✅ Kyllä | Nopea, alle minuutin toimenpide |
| Kauden tilanteen tarkistaminen | ✅ Kyllä | Yhteenveto näkyy heti etusivulla |
| Virheellisen tuloksen korjaaminen | ✅ Kyllä | Muokkaus onnistuu suoraan listalta |

---

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

---

### Missä ratkaisu jäi vajaaksi?

**Datan pysyvyys:** Tiedot tallennetaan selaimen local storageen, joten ne häviävät jos selain tyhjennetään tai vaihdetaan. Oikeassa tuotantokäytössä tarvittaisiin pilvipalvelu tai tiedostovienti.

**Yhden käyttäjän rajoitus:** Sovellus on suunniteltu yhdelle käyttäjälle. Joukkueen kaikki pelaajat eivät näe samoja tietoja, ellei sovellusta laajenneta tietokannalla ja kirjautumisella.

**Ei varmuuskopiointia:** Käyttäjällä ei ole mahdollisuutta viedä tietoja esim. CSV-tiedostona tai jakaa niitä muille.

---

### Kokonaisarvio

Sovellus ratkaisee alkuperäisen ongelman hyvin demokäytössä ja henkilökohtaisessa seurannassa. Se on teknisesti toimiva, helppokäyttöinen ja vastaa kaikkiin määriteltyihin vaatimuksiin. Jatkokehityskohteina datan pysyvyys ja monen käyttäjän tuki olisivat luontevia seuraavia askelia.
