# Ceny za 1m2 mieszkań w województwach w Polsce

## Spis treści
* [Wprowadzenie](#Wprowadzenie)
* [Technologie](#Technologie)
* [Wyniki](#Wyniki)
* [Status](#Status)

## Wprowadzenie
Celem projektu jest wyestymowanie modelu najlepiej wyjaśniającego ceny za 1m2 mieszkań w województwach w Polsce w latach 2010 – 2020. Estymację modeli przeprowadzano z użyciem programu GRETL.

Dane wykorzystane w projekcie w całości pochodzą ze strony Banku Danych Lokalnych1. Dane dotyczą wartości rocznych zmiennych w latach 2010 – 2020 dla wszystkich województw w Polsce
Zmienną objaśnianą w badaniu była 𝑚𝑖𝑒𝑠𝑧, czyli średnia cena 1m2 lokali mieszkalnych. Po analizie wpływu zmiennych na ceny mieszkań wybrano 11 zmiennych objaśniających, które potencjalnie mogą wpływać na zmienną objaśnianą. Poniżej przedstawiono wybrany zbiór danych wraz z opisem.
• miesz - średnia cena za 1 m2 lokali mieszkalnych
• wynag – średnie miesięczne wynagrodzenie brutto
• komun - przewozy pasażerskie przypadający na 1 osobę w ciągu roku
• drogi - drogi publiczne ogółem o nawierzchni twardej i gruntowej (w tys. km)
• lud – liczba ludności (w mln)
• turys - noclegi udzielone turystom zagranicznym (nierezydentom) w turystycznych obiektach noclegowych (w tys.)
• urban - ludność w miastach w % ogółu ludności
• inf – wskaźnik inflacji
• bezrob - stopa bezrobocia rejestrowanego (liczba bezrobotnych zarejestrowanych w stosunku do ogólnej liczby ludności w danym województwie w danym roku)
• lek - lekarze (personel pracujący ogółem) na 100 tys. ludności
• skol - współczynnik skolaryzacji netto w szkołach podstawowych (liczba uczniów szkół podstawowych w wieku 7-15 lat na początku danego roku szkolnego przez liczbę ludności w wieku 7-15 lat według stanu w dniu 31 XII tego samego roku; wynik podany w ujęciu procentowym)
• kina - liczba ludności na 1 miejsce w kinach stałych
Zmienne takie jak inflacja, stopa bezrobocia i średnie zarobki bardzo dobrze oddają sytuację ekonomiczną województwa w danym roku. Jako potencjalnych kandydatów wybrano również stopień urbanizacji i liczba ludności, które miały oddawać tendencje do osiedlania w miejscach o większym nagromadzeniu ludzi. Kolejnymi wskaźnikami, które wzięto pod uwagę był dostęp do komunikacji oraz liczba dróg (w kilometrach). Zmienne te miały oddawać stopień skomunikowania. Na warunki życia zdecydowanie wpływa również dostępność do służby zdrowia, edukacji oraz szeroko pojętej kultury. Wpływy uwzględniono poprzez dodanie w badaniu zmiennych 𝑙𝑒𝑘,𝑠𝑘𝑜𝑙 oraz 𝑘𝑖𝑛𝑎 (jako wskaźnik dostępu do kultury). Dzięki temu sprawdzono, czy ceny mieszkań można wyjaśnić za pomocą turystyki w danym województwie.

Projekt rozpoczęto od zapoznania się z danymi. W pracy zostały zobrazowane zależności między zmianną objaśnianą i objaśniającymi oraz statystyki opisowe poszczególnych zmiannych. Sprawdzono również korelacje między zmiannymi - wizualnie oraz numerycznie. Można zauważyć silną korelację pomiędzy zmienną objaśnianą i zmiennymi 𝑤𝑦𝑛𝑎𝑔,𝑘𝑜𝑚𝑢𝑛,𝑑𝑟𝑜𝑔𝑖,𝑙𝑢𝑑,𝑡𝑢𝑟𝑦𝑠,𝑙𝑒𝑘. Niestety zanotowano również niepożądane korelacje. Zmienna 𝑘𝑖𝑛𝑜 silnie korelowała ze zmiennymi 𝑤𝑦𝑛𝑎𝑔, 𝑘𝑜𝑚𝑢𝑛,𝑑𝑟𝑜𝑔𝑖 oraz 𝑙𝑢𝑑. Z tego powodów postanowiono wyłączyć ją z dalszej analizy. Podobnie zaobserwowano korelację między zmienną 𝑏𝑒𝑧𝑟𝑜𝑏, a zmienną wynagrodzenie. Zmienną 𝑏𝑒𝑧𝑟𝑜𝑏 również wyłączono z dalszej analizy.

Z uwagi na to, że zmienne 𝑚𝑖𝑒𝑠𝑧 oraz 𝑡𝑢𝑟𝑦𝑠 charakteryzowały się dużą asymetrią rozkładu, a dodatkowo zmienna 𝑡𝑢𝑟𝑦𝑠 przyjmowała duże wartości w analizie postanowiono użyć logarytmów zmiennych

Podsumowując w estymacji modelu nie brano pod uwagę zmiennych 𝑖𝑛𝑓 oraz 𝑠𝑘𝑜𝑙 ze względu na mały stopień zmienności danych oraz zmiennych 𝑏𝑒𝑧𝑟𝑜𝑏 i 𝑘𝑖𝑛𝑎 ze względu na duży współczynnik korelacji z pozostałymi zmiennymi objaśniającymi. W dalszej analizie użyto ostatecznie 7 zmiennych objaśniających.

W drugiej części pracy wyestomowano model regresji łącznej, model efektów ustalonych (FE) oraz model efektów losowych (RE). Następnie sprawdzono również zasadność modelu dwukierunkowego z dołożonymi efektami czasowymi. Na koniec przetestowano również zasadność stosowania modeli dynamicznych. Szczegółowe wyniki oraz uzasadnienie wyboru najlepszego modelu zaprezentowano w pracy. 

[Pełna analiza](https://github.com/Lukkud/Multidimensional_panel_data/blob/main/Lukasz_Chuchra_projekt.pdf)

## Technologie 
* GRETL

## Wyniki
Ostatecznie wybrano dwukierunkowy model efektów ustalonych postaci

? panel new_new_l_miesz const new_new_wynag new_new_drogi new_new_lud \par --time-dummies

Model 34: Estymacja Ustalone efekty, z wykorzystaniem 128 obserwacji  
Włączono 16 jednostek danych przekrojowych  
Szereg czasowy długości = 8  
Zmienna zależna (Y): new_new_l_miesz  
Z powodu ścisłej współliniowości pominięto zmienną: dt_10  
| | współczynnik | błąd standardowy | t-Studenta | wartość p |
|-|------------|-------------------|------------|-----------|
| const | 1.90948 | 0.445943 | 4.282 | 4.20e-05 *** |
| new_new_wynag | 0.0768222 | 0.0310217 | 2.476 | 0.0149 ** |
| new_new_drogi | 0.0116117 | 0.00633673 | 1.832 | 0.0698 * |
| new_new_lud | −1.08687 | 0.299107 | −3.634 | 0.0004 *** |
| dt_3 | −0.0754806 | 0.0260150 | −2.901 | 0.0046 *** |
| dt_4 | −0.0803809 | 0.0245350 | −3.276 | 0.0014 *** |
| dt_5 | −0.0755428 | 0.0228897 | −3.300 | 0.0013 *** |
| dt_6 | −0.0724183 | 0.0211869 | −3.418 | 0.0009 *** |
| dt_7 | −0.0781904 | 0.0194404 | −4.022 | 0.0001 *** |
| dt_8 | −0.0617649 | 0.0159297 | −3.877 | 0.0002 *** |
| dt_9 | −0.0178809 | 0.0130673 | −1.368 | 0.1742 |

Średn.aryt.zm.zależnej 0.701042  
Odch.stand.zm.zależnej 0.384841  
Suma kwadratów reszt 0.109870  
Błąd standardowy reszt 0.032820  
LSDV R-kwadrat 0.994159 Within R-kwadrat 0.788423  
LSDV F(25, 102) 694.3895 Wartość p dla testu F 1.4e-102  

Logarytm wiarygodności 270.2469  
Kryt. inform. Akaike'a −488.4939  
Kryt. bayes. Schwarza −414.3411   
Kryt. Hannana-Quinna −458.3652  

Autokorel.reszt - rho1 0.091738 Stat. Durbina-Watsona 1.461362  
Joint test on named regressors -  
Statystyka testu: F(3, 102) = 13.3097  
z wartością p = P(F(3, 102) > 13.3097) = 2.12466e-007  

Test na zróżnicowanie wyrazu wolnego w grupach -  
Hipoteza zerowa: grupy posiadają wspólny wyraz wolny  
Statystyka testu: F(15, 102) = 34.0441  
z wartością p = P(F(15, 102) > 34.0441) = 6.50103e-033  

Test Walda na łączną istotność zmiennych 0-1 jednostek czasu -  
Hipoteza zerowa: No time effects  
Asymptotyczna statystyka testu: Chi-kwadrat(7) = 24.0529  
z wartością p = 0.00111523  

Model charakteryzuje się współczynnikiem determinacji 𝑅2=0.99 oraz wewnątrzgrupowym 𝑅2=0.79. Niestety w trakcie usuwania autokorelacji z modelu wyjściowego reszty utraciły charakter rozkładu normalnego, co powoduje, że nie ma możliwości oszacowania istotności zmiennych modelu.
Analiza innych modeli (jednokierunkowych oraz dynamicznych) również nie przyniosła lepszych rezultatów.
W modelu nie występuje autokorelacja reszt modelu, a także heteroskedastyczność.

Testowanie modeli wskazało, że model FE był lepszy od modeli regresji łącznej oraz efektów losowych.
Ze względu na brak normalnego rozkładu reszt nie przeprowadzono interpretacji współczynników przy zmiennych.

[Pełna analiza](https://github.com/Lukkud/Multidimensional_panel_data/blob/main/Lukasz_Chuchra_projekt.pdf)

## Status
Projekt zakończony
