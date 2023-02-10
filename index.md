<meta http-equiv='cache-control' content='no-cache'> 
<meta http-equiv='expires' content='0'> 
<meta http-equiv='pragma' content='no-cache'>

# Les meilleures audiences dans les salles de cinéma françaises
## *Cette présentation vise à montrer les scores d'audience réalisés par les 200 films les plus plébiscités dans les salles françaises, sur une période allant de 1945 à 2021*

*Sommaire*
- Avant-Propos
- 1)Jeu de données utilisé
- 2)Visualisations
  * 2) a.Scatter dots des scores réalisés par les films les plus populaires au cinéma en France de 1945 à 2021
  * 2) b.Grid of pie charts présntant une répartition par année des plus gros succès et de leur chiffres au box office
  * 2) c.Area chart du nombre d'entrées cumulées par années
  * 2) d.Réalisateurs ayant comptabilisé le plus d'entrées dans les salles françaises
  * 2) e.Wikidata Query Service
- Conclusion

**Avant-Propos**

La France, tant dans sa production que dans sa consommation, est un des acteurs mondiaux les plus conséquents du marché du Cinéma :
> La France était en 2013 le deuxième exportateur de films au monde derrière les États-Unis et une étude réalisée en avril 2014 montre l'excellente image dont bénéficie le cinéma français à travers le monde, qui reste le cinéma le plus apprécié après le cinéma américain [...]
Avec 200 millions de billets vendus en 2012, et environ 213 millions attendus en 2015, la France est actuellement le troisième marché du cinéma mondial, que ce soit en termes d'entrées (derrière les États-Unis et l'Inde), ou en termes de revenus (derrière les États-Unis et le Japon). 
[<sub>Wikipédia</sub>](https://fr.wikipedia.org/wiki/Cin%C3%A9ma_fran%C3%A7ais#Audience_contemporaine)

Et pour cause, en 2020, 2041 salles de cinéma sont recensées sur l'ensemble du territoire français, comptabilisant un total de 6127 écrans, et 1 138 530 sièges[^1]. Bien que ces chiffres soient conséquents, il faut noter qu'ils sont en baisse considérable en comparaison des années précédentes, en raison de la crise sanitaire, comme il apparaît dans ces [tableaux](https://fr.wikipedia.org/wiki/Cin%C3%A9ma_fran%C3%A7ais#Exploitation) :

<table class="wikitable centre">
<caption>Exploitation cinématographique en France
</caption>
<tbody><tr>
<td>
</td>
<th scope="col"><a href="/wiki/2003_au_cin%C3%A9ma" title="2003 au cinéma">2003</a>
</th>
<th scope="col"><a href="/wiki/2004_au_cin%C3%A9ma" title="2004 au cinéma">2004</a>
</th>
<th scope="col"><a href="/wiki/2005_au_cin%C3%A9ma" title="2005 au cinéma">2005</a>
</th>
<th scope="col"><a href="/wiki/2006_au_cin%C3%A9ma" title="2006 au cinéma">2006</a>
</th>
<th scope="col"><a href="/wiki/2007_au_cin%C3%A9ma" title="2007 au cinéma">2007</a>
</th>
<th scope="col"><a href="/wiki/2008_au_cin%C3%A9ma" title="2008 au cinéma">2008</a>
</th>
<th scope="col"><a href="/wiki/2009_au_cin%C3%A9ma" title="2009 au cinéma">2009</a>
</th>
<th scope="col"><a href="/wiki/2010_au_cin%C3%A9ma" title="2010 au cinéma">2010</a>
</th>
<th scope="col"><a href="/wiki/2011_au_cin%C3%A9ma" title="2011 au cinéma">2011</a>
</th>
<th scope="col"><a href="/wiki/2012_au_cin%C3%A9ma" title="2012 au cinéma">2012</a>
</th></tr>
<tr>
<th scope="row">Nombre d'établissements
</th>
<td align="center">2&#160;130
</td>
<td align="center">2&#160;100
</td>
<td align="center">2&#160;076
</td>
<td align="center">2&#160;063
</td>
<td align="center">2&#160;054
</td>
<td align="center">2&#160;068
</td>
<td align="center">2&#160;065
</td>
<td align="center">2&#160;046
</td>
<td align="center">2&#160;032
</td>
<td align="center">2&#160;029
</td></tr>
<tr>
<th scope="row">Nombre de multiplexe (+8 salles)
</th>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">158
</td>
<td align="center">164
</td>
<td align="center">171
</td>
<td align="center">172
</td>
<td align="center">176
</td>
<td align="center">
</td></tr>
<tr>
<th scope="row">Nombre d'écrans actifs
</th>
<td align="center">5&#160;281
</td>
<td align="center">5&#160;276
</td>
<td align="center">5&#160;273
</td>
<td align="center">5&#160;283
</td>
<td align="center">5&#160;315
</td>
<td align="center">5&#160;389
</td>
<td align="center">5&#160;469
</td>
<td align="center">5&#160;464
</td>
<td align="center">5&#160;466
</td>
<td align="center">5&#160;502
</td></tr>
<tr>
<th scope="row">Nombre de fauteuils
</th>
<td align="center">1&#160;073&#160;000
</td>
<td align="center">1&#160;061&#160;669
</td>
<td align="center">1&#160;059&#160;264
</td>
<td align="center">1&#160;056&#160;868
</td>
<td align="center">1&#160;056&#160;072
</td>
<td align="center">1&#160;066&#160;593
</td>
<td align="center">1&#160;076&#160;984
</td>
<td align="center">1&#160;073&#160;681
</td>
<td align="center">1&#160;065&#160;803
</td>
<td align="center">1&#160;068&#160;903
</td></tr>
<tr>
<th scope="row">Nombre d'entrées (millions)
</th>
<td align="center">173,46
</td>
<td align="center">195,69
</td>
<td align="center">175,52
</td>
<td align="center">188,77
</td>
<td align="center">178,41
</td>
<td align="center">190,18
</td>
<td align="center">201,51
</td>
<td align="center">206,95
</td>
<td align="center">217,07
</td>
<td align="center">203,44
</td></tr>
<tr>
<th scope="row">Recette totale en salle
</th>
<td align="center">996,11&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;138,94&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;031,2&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;120,7&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;061,52&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;142,21&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;236,41&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;308,92&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;373,92&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;305,63&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td></tr>
<tr>
<th scope="row">Part de marché des films<br />français dans les recettes
</th>
<td align="center" valign="middle">34,9&#160;%
</td>
<td align="center" valign="middle">38,4&#160;%
</td>
<td align="center" valign="middle">36,5&#160;%
</td>
<td align="center" valign="middle">44,6&#160;%
</td>
<td align="center" valign="middle">36,5&#160;%
</td>
<td align="center" valign="middle">45,4&#160;%
</td>
<td align="center" valign="middle">36,8&#160;%
</td>
<td align="center" valign="middle">35,8&#160;%
</td>
<td align="center" valign="middle">40,9&#160;%
</td>
<td align="center" valign="middle">40,3&#160;%
</td></tr></tbody></table>

<table class="wikitable centre">
<tbody><tr>
<td>
</td>
<th scope="col"><a href="/wiki/2013_au_cin%C3%A9ma" title="2013 au cinéma">2013</a>
</th>
<th scope="col"><a href="/wiki/2014_au_cin%C3%A9ma" title="2014 au cinéma">2014</a>
</th>
<th scope="col"><a href="/wiki/2015_au_cin%C3%A9ma" title="2015 au cinéma">2015</a>
</th>
<th scope="col"><a href="/wiki/2016_au_cin%C3%A9ma" title="2016 au cinéma">2016</a>
</th>
<th scope="col"><a href="/wiki/2017_au_cin%C3%A9ma" title="2017 au cinéma">2017</a>
</th>
<th scope="col"><a href="/wiki/2018_au_cin%C3%A9ma" title="2018 au cinéma">2018</a>
</th>
<th scope="col"><a href="/wiki/2019_au_cin%C3%A9ma" title="2019 au cinéma">2019</a>
</th>
<th scope="col"><a href="/wiki/2020_au_cin%C3%A9ma" title="2020 au cinéma">2020</a>
</th></tr>
<tr>
<th scope="row">Nombre d'établissements
</th>
<td align="center">2&#160;026
</td>
<td align="center">2&#160;020
</td>
<td align="center">2&#160;033
</td>
<td align="center">2&#160;044
</td>
<td align="center">2&#160;046
</td>
<td align="center">2040
</td>
<td align="center">2045
</td>
<td align="center">2041
</td></tr>
<tr>
<th scope="row">Nombre de multiplexe (+8 salles)
</th>
<td align="center">188
</td>
<td align="center">191
</td>
<td align="center">203
</td>
<td align="center">209
</td>
<td align="center">219
</td>
<td align="center">226
</td>
<td align="center">232
</td>
<td align="center">233
</td></tr>
<tr>
<th scope="row">Nombre d'écrans actifs
</th>
<td align="center">5&#160;588
</td>
<td align="center">5&#160;653
</td>
<td align="center">5&#160;741
</td>
<td align="center">5&#160;842
</td>
<td align="center">5&#160;913
</td>
<td align="center">5982
</td>
<td align="center">6114
</td>
<td align="center">6127
</td></tr>
<tr>
<th scope="row">Nombre de fauteuils
</th>
<td align="center">1&#160;066&#160;840
</td>
<td align="center">1&#160;072&#160;407
</td>
<td align="center">1&#160;094&#160;703
</td>
<td align="center">1&#160;099&#160;526
</td>
<td align="center">1&#160;118&#160;916
</td>
<td align="center">1&#160;126&#160;162
</td>
<td align="center">1&#160;140&#160;999
</td>
<td align="center">1&#160;138&#160;530
</td></tr>
<tr>
<th scope="row">Nombre d'entrées (millions)
</th>
<td align="center">193,6
</td>
<td align="center">208,9
</td>
<td align="center">205,3
</td>
<td align="center">213,2
</td>
<td align="center">209,2
</td>
<td align="center">201,20
</td>
<td align="center">213.0
</td>
<td align="center">65;1
</td></tr>
<tr>
<th scope="row">Recette totale en salle
</th>
<td align="center">1&#160;250,87&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;332,73&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;331,3&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;388,6&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1&#160;380,6&#160;<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1336,73<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center">1447,4<abbr class="abbr" title="mégaeuro">M€</abbr>
</td>
<td align="center"><abbr class="abbr" title="mégaeuro">M€</abbr>
</td></tr>
<tr>
<th scope="row">Part de marché des films<br />français dans les recettes
</th>
<td align="center" valign="middle">33,8&#160;%
</td>
<td align="center" valign="middle">44,5&#160;%
</td>
<td align="center" valign="middle">35,5&#160;%
</td>
<td align="center" valign="middle">35,8&#160;%
</td>
<td align="center" valign="middle">37,4&#160;%
</td>
<td align="center" valign="middle">39,3%
</td>
<td align="center" valign="middle">34,8&#160;%
</td>
<td align="center" valign="middle">44.9%
</td></tr></tbody></table>

En 1946, dans un soucis d'encadrer et de restaurer le cinéma français fortement impacté au crépuscule de la Seconde Guerre Mondiale, est fondé le Centre National du Cinéma et de l'image animée, dit CNC. Depuis 1968, suite à un arrêté imposant l’inventaire précis des collections bénéficiant de crédits publics, le CNC assure un suivi archivistique rigoureux des oeuvres et des données relatives au cinéma français. Ces données sont publiées depuis 2014 sur [la plateforme _opendata_ du gouvernement](https://www.data.gouv.fr/fr/).

**1) Jeu de données utilisé** 

Afin de pouvoir l'exploiter, j'ai dû procéder à un nettoyage de ce fichier xlsx car il ne s'accordait pas aux bonnes pratiques; des cellules étaient fusionnées, les données ne commencaient pas aux premières lignes du tableau, les valeurs numériques étaient décimales, ce qui faussait les visualisations. La plus grande difficulté que j'ai rencontré lors du _sanity check_ était la correction du format des valeurs dans la colonne "année de sortie". Elles étaient traitées comme des valeurs numériques décimales, il était donc impossible pour les outils de visualition de les traiter comme des dates. J'ai donc dû utiliser, sur OpenRefine, le langage GREL, pour arrondir les valeurs avec la fonction `value.round()` avant de convertir leur format en date grâce à la fonction `value.toDate()`, ce qui me retournait une date sous ce format : 
> [date 1998-01-01T00:00:00Z]

J'ai donc utilisé la fonction `value.datePart("year")` pour extraire et afficher uniquement l'année.

Voici le jeu de données tel qu'il était en accès libre :

<iframe src="https://www.data.gouv.fr/fr/datasets/r/73d60fd5-c1f3-4a59-8d82-bd06d4afd077" width="850" height="600" frameborder="0"></iframe> 

Et en voici un extrait après les modifications mentionnées plus haut sur OpenRefine :

<meta charset= "utf-8" />
<table width="600" height="450" frameborder ="0">
<tr><th>Rang</th><th>Titre</th><th>réalisateur</th><th>année de sortie</th><th>nationalité</th><th>nombre d'entrées en millions</th></tr>
<tr><td>1</td><td>Titanic</td><td>J. Cameron</td><td>1998</td><td>US</td><td>21798906</td></tr>
<tr><td>2</td><td>Bienvenue chez les Ch&apos;tis</td><td>D. Boon</td><td>2008</td><td>FR</td><td>20444918</td></tr>
<tr><td>3</td><td>Intouchables</td><td>E. Tolédano, O. Nakache</td><td>2011</td><td>FR</td><td>19509835</td></tr>
<tr><td>4</td><td>La Grande Vadrouille</td><td>G. Oury</td><td>1966</td><td>FR/GB</td><td>17330139</td></tr>
<tr><td>5</td><td>Autant en emporte le vent</td><td>V. Fleming</td><td>1950</td><td>US</td><td>16728160</td></tr>
<tr><td>6</td><td>Il était une fois dans l&apos;Ouest</td><td>S. Leone</td><td>1969</td><td>IT</td><td>14891828</td></tr>
<tr><td>7</td><td>Le Livre de la jungle</td><td>W. Reitherman</td><td>1968</td><td>US</td><td>14798057</td></tr></table>



**2) Visualisations**

   **a. Scattered dots des scores réalisés par les films les plus populaires au cinéma en France de 1945 à 2021**

<iframe src='https://public.flourish.studio/visualisation/12691863/embed' title='Score réalisés par les films les plus populaires au cinéma en France de 1945 à 2021' frameborder='0' scrolling='no' style='width:100%;height:450px;'></iframe>

   **b. Grid of pie charts: Répartition par année des plus gros succès et de leur chiffres au box office**
   
<iframe src='https://public.flourish.studio/visualisation/12692271/embed' title='Répartition par année des plus gros succès et de leur chiffres au box office' frameborder='0' scrolling='yes' style='width:100%;height:600px;'></iframe>

  
   **c. Réalisateurs ayant comptabilisé le plus d'entrées dans les salles françaises**
    
<iframe src='https://public.flourish.studio/visualisation/12706313/embed' title='Vision globale des réalisateurs et des performances de leurs films' frameborder='0' scrolling='no' style='width:100%;height:600px;'></iframe>

  
   **d. Le Cinéma Français à l'international avec Wikidata Query Service**
   
L'analyse de ces données laisse clairement transparaître l'enthousiasme des français pour le grand écran, tant du côté des spectateurs que de celui des créateurs. Cependant, elle soulève également d'autres questions. On pourrait par exemple se demander ce qu'il en est du succès - ou non - du cinéma français contemporain à l'international, en compaaison avec les autres pays. Pour obtenir des données pertinentes à ce sujet, il a fallu interroger la base de données Wikidata. J'ai formulé la requête suivante :
```SPARQL

#création de colonnes qui renseignent : le pays d'origine, les chiffres au box office, ainsi que les noms de ces films
SELECT DISTINCT ?item ?origincountry ?boxoffice ?name  WHERE {
  ?item rdfs:label ?name;
        wdt:P31 wd:Q11424; #déclaration des titres comme étant de nature "film"  
        wdt:P577 ?publication_date; #indication de leur date de publication
        wdt:P2142 ?boxoffice. #indication de leurs chiffres au box office
  OPTIONAL {
    ?item wdt:P495 ?Qorigincountry. 
    ?Qorigincountry rdfs:label ?origincountry. #affichage du nom du pays d'origine en français
    FILTER((LANG(?origincountry)) = "fr")   
  }       
  
  FILTER(xsd:date(?publication_date) > "2022-01-01"^^xsd:date) 
  FILTER ( lang(?name) = "fr")
 }
ORDER BY ?boxoffice #limitation de la requête aux films sortis depuis le début de l'année 2022, dont on veut le titre en français

```
J'ai ainsi pu obtenir les données suivantes :
<iframe style="width: 80vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23%20cr%C3%A9ation%20de%20colonnes%20qui%20renseignent%20%3A%20le%20pays%20d%27origine%2C%20les%20chiffres%20au%20box%20office%2C%20ainsi%20que%20les%20noms%20de%20ces%20films%0ASELECT%20DISTINCT%20%3Fitem%20%3Forigincountry%20%3Fboxoffice%20%3Fname%20%20WHERE%20%7B%0A%20%20%3Fitem%20rdfs%3Alabel%20%3Fname%3B%0A%20%20%20%20%20%20%20%20wdt%3AP31%20wd%3AQ11424%3B%20%23%20d%C3%A9claration%20des%20titres%20comme%20%C3%A9tant%20de%20nature%20%22film%22%0A%20%20%20%20%20%20%20%20wdt%3AP577%20%3Fpublication_date%3B%20%23%20indication%20de%20leur%20date%20de%20publication%0A%20%20%20%20%20%20%20%20wdt%3AP2142%20%3Fboxoffice.%20%23%20indication%20de%20leurs%20chiffres%20au%20box%20office%0A%20%20OPTIONAL%20%7B%0A%20%20%20%20%3Fitem%20wdt%3AP495%20%3FQorigincountry.%20%23%20affichage%20du%20nom%20du%20pays%20d%27origine%0A%20%20%20%20%3FQorigincountry%20rdfs%3Alabel%20%3Forigincountry.%0A%20%20%20%20FILTER%28%28LANG%28%3Forigincountry%29%29%20%3D%20%22fr%22%29%20%23%20en%20fran%C3%A7ais%20%20%0A%20%20%7D%0A%23%20limitation%20de%20la%20requ%C3%AAte%20aux%20films%20sortis%20depuis%20le%20d%C3%A9but%20de%20l%27ann%C3%A9e%202022%2C%20dont%20on%20veut%20le%20titre%20en%20fran%C3%A7ais%20%20%20%20%20%20%20%20%0A%20%20FILTER%28xsd%3Adate%28%3Fpublication_date%29%20%3E%20%222022-01-01%22%5E%5Exsd%3Adate%29%0A%20%20FILTER%20%28%20lang%28%3Fname%29%20%3D%20%22fr%22%29%0A%20%7D%0AORDER%20BY%20%3Fboxoffice%20%23%20classement%20par%20chiffre%20r%C3%A9alis%C3%A9%0A%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

La visualisation en bar chart laisse transparaître la dominance écrasante des Etats-Unis sur le marché du cinéma, dont les recettes totales des films de 2022 au box office s'élèvent à plus de 22 milliards de dollars. Le box office des films français se classent néanmoins à la cinquième place ; mais avec une différence abyssale, en s'élevant à moins d'un milliard de dollars. Après étude de cette visualisation, on peut émettre certaines hypothèses ; en effet, les pays qui sont avant la France au classement sont les Etats-Unis, le Royaume-Uni, la Chine et l'Australie. Trois d'entre eux ont la même langue, l'anglais, qui est la deuxième la plus utilisée au monde, tandis que le chinois est la langue la plus parlée au monde. Ce facteur explique assurèment les succès des films de ces pays.

**Conclusion**

Ce projet a été intéressant bien que chronophage et complexe. L'analyse de ces données a été enrichissante en ce qu'elle a été l'occasion de se rendre compte de la conséquence du marché du cinéma. Il engage des chiffres astronomiques qu'ils s'agissent des recettes, qui se comptent en milliards, ou des fréquentations des salles, rien que sur l'échelle d'un seul pays.

[^1]: [Wikipédia](https://fr.wikipedia.org/wiki/Cin%C3%A9ma_fran%C3%A7ais#Exploitation)

