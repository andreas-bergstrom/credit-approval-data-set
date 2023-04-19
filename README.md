# credit-approval-data-set
ML-model for credit approval prediction

## Problemet

De flesta företag jobbar med någon slags kreditgivning och där vill man hålla nere risken för kreditförluster. Förvånande nog så har rena kreditupplysningstjänster inga jättebra ML-baserade tjänster, utan levererar bara sin "kreditscore" som man gjort sedan tidens början. En uppsjö av tredjeparts-leverantörer för detta finns, men här vill vi ta fram en modell för att avgöra om en kreditansökan ska godkännas eller inte utifrån historiska ansökningsresultat.

Datan kommer alltså vara själva ansökningsresultatet. Optimalt hade vi även önskat att få med betalningshistoriken för varje godkänd ansökan (ex. om de fullföljde betalning eller blev en kreditförlust), men det är ännu oklart om det går att få tag på i närtid. Därför nöjer vi oss med data fram till godkänd eller nekad ansökning.

## Lösningsförslag

- Tvätta och normalisera data efter undersökning
- Angripa problemet med supervised learning, men även utforska unsupervised och se vilka ev. oväntande samband som finns
- Testa olika modeller, från enkel KNN klassificering till Decision Tree och random forest
- Driftsätt en modell på AWS Lambda och/eller http://streamlit.io för att kunna använda ny data och se resultat

## Datan

För denna uppgift kommer riktig data från min arbetsplats att användas, men då det är känslig info även om allt anonymiseras så kommer jag för denna projektinlämning att använda ett annat dataset parallellt för inlämningen. Datasetet består av rader av ansökningar med olika data från egen kundkännedom (tidigare ordrar, summor, senaste order, etc.) samt inhämtad kreditupplysning från Creditsafe. Data finns sedan 15 år bakåt men då riktlinjer ändrats genom åren är endast de 3 senaste relevanta. Viss grad av bortfiltrering behöver göras då ex. många restauranger nekades våren 2020 iom. pandemi-nedstängingen. 

Det finns också en del extremvärden i form av uppenbara bedrägeri-orders på alldelens för stora summor, ofta från företagskunder med god historik men där det är magkänslan som indikerar att något inte stämmer. Då vi vill fokusera på ren kreditbedömning och inte att avgöra bedrägerier som kommer även dessa bedrägeri-märkta rader att exkluderas.

För inlämningen har jag kollat runt efter liknande dataset och hittat detta men ungefär samma format där sista kolumnen är nekad/godkänd:
https://archive.ics.uci.edu/ml/datasets/credit+approval
