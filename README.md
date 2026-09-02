---------------------
Opdateringer 2/9-2026

# Copilot status (2026-09-02)
Her er en kort status og forslag baseret på de øverste opdateringer i README:

- Dataopbevaring ("Hvor gemmer du data henne?"): Beslutning nødvendig. Forslag: brug delt Google Sheets (brugervenligt) eller en Git-tracked JSON/CSV i repoet (bedre til automation). Jeg kan implementere eksport/import til begge formater.
  - Action: vent på valg fra dig.

- Helligdage ("hvor er helligdagene blevet af?"): Mangler i nuværende kode. Forslag: tilføj en `holidays`-liste der bruges ved generering af ugedatoer, så helligdage fremhæves eller markeres som "fri".
  - Action: jeg kan tilføje en simpel holiday-array og markering i tabellen.

- Ferie-registrering og status-koder (Dorte FO dage / SH / FE): Der nævnes flere kategorier.
  - Forslag: tilføj checkbokse / statuskoder (FO, FE, A9, sygdom, TJ) i dag-redigeringsmodalen og en forklaring i legend.
  - Action: implementeres efter prioritet/ønske.

- Ugenummer på print ("hvorfor kan man ikke se ugenummer på printet?"): Print-styling skjuler nogle controls, men ugenummer kan indsættes i header (statisk tekst) så det følger med ved print.
  - Action: jeg kan tilføje ugenummer i header og sikre print CSS viser det.

- Gemt paragraf med info (normperiode, timer og status): God idé. Forslag: gem normperiode og timer i localStorage eller i separate fil (fx SETTINGS.json) og vis som en permanent paragraf over tabellen.
  - Action: jeg kan tilføje visning + mulighed for at gemme fra adminpanelet.

- Fjern kassen med "½ time korte dage": Der står at den skal fjernes.
  - Action: jeg vil fjerne visningen fra stats/controls og beregninger.

- div.legend navne opdaterer ikke: Bug. Sandsynlig årsag: legend-elementerne opdateres ikke i updateSchedule().
  - Action: jeg retter updateSchedule() så #vagtNavnN opdateres fra vagter-konfigurationen.

- Rul-problem (3 medarbejdere til 4 vagter): Sandsynlig rotationslogik-fejl; hvis der er flere vagter end personer, skal nogle gentages eller rotationsalgoritmen justeres.
  - Action: Jeg gennemgår rotationsalgoritmen og foreslår at rotationList altid styrer navnene per vagt pr. uge; kan også understøtte forskudt start.

Næste skridt jeg kan tage nu (vælg eller bekræft):
1) Implementere de mindre ændringer: opdatere legend-navne, fjerne kort-dagsfelt, vise ugenummer ved print og gemme normperiode-tekst i header (commit direkte til main).
2) Implementere data/ferie-håndtering og holiday-markering (kræver flere valg; jeg laver en PR).
3) Ingen ændring: blot dokumentere videre (jeg venter på din bekræftelse).

Skriv hvilken af 1/2/3 du vil jeg skal gøre nu, eller svar med præcis hvor meget du vil have implementeret (fx "Gør 1 og 2, men lav PR for 2").

---------------------

Hvor gemmer du data henne.
Kan et delt excel ark gøre det?

hvor er helligdagene blevet af?

ferie registrering Dorte FO dage - Alle andre SH - FE  dage
Måske flere check bokse (FO, FE, A9, sygdom, TJ) og så skal det beskrive hvad der er hvad.

hvorfor kan man ikke se ugenummer på printet?

Kan du eventuelt tilføje en gemt paragraf med info (norm periode, timer og status)?

Kassen med ½ time korte dage skal fjernes.

div.legend, navne opdaterer ikke med listen. 
Kan det fixes. hvis ikke så fjern dem.

fik du set på rul problemet? 3 medarbejdere til 4 vagter?

Du er velkommen til at opdatere denne fil efterhånden som opdateringerne bliver lavet.
Ellers gør jeg det når jeg ser dem virke.

Done --------------------------------
Dette er baseret på en tidligere løsning.

Oplæg fra Dorte:
Backend til at bytte vagter på dags niveau så jeg tænker at skemaet oprettes og så tilføjes der navne efterfølgende

vagter:
1. 7 - 15
2. 8 - 16
5. 9 - 16:60 - Admi
3. 10 - 18
4. 12 - 20
Alle vagter mandag til fredag. Der er ikke arbejde i weekenden.

Senere skal dette tilføjes
Norm periode
over 16 uger (fx 37*16 = 592 timer)
Hvornår går perioden fra og til.

1 valgfri ½ time kortere arbejdsdag pr uge.

