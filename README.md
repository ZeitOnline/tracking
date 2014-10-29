# ZEIT ONLINE Tracking

Im ZEIT ONLINE Umfeld werden regelmäßig verschiedene Verpixelungskonzepte eingesetzt, die hier beispielhaft beschrieben sind. Alle Codebeispiele finden sich auch als Download in diesem Repository und werden auf dem aktuellen Stand gehalten.

## Verortung der Scripte
Da wir bei einem werblichen Umfeld möglichst hohe Abrufzahlen vermelden wollen, bitte alle Scripte im HTML möglichst weit oben platzieren.

## IVW
Grunssätzlich gilt:
```html
<script type="text/javascript" src="https://script.ioam.de/iam.js"></script>
<!--SZM VERSION="2.0"-->
<script type="text/javascript">
    var iam_data = {
        'st' : 'zeitonl', // site/domain
        'cp' : 'angebote/urlaubsziele/bild-text', // seitencode
        'sv' : 'i2', // Befragungseinladung
        'co' : 'URL: marktplatz.zeit.de/urlaubsziele/' // comment
    }
    iom.c(iam_data,1); 
</script>
```

## Google Analytics
Grunssätzlich gilt:
```html
<!--start: google analytics tracker-->
<div class="ga_tracker">
    <script type="text/javascript">
        var _gaq = _gaq || []; 
        _gaq.push(['_setAccount', 'UA-18122964-1']); 
        _gaq.push(['_setDomainName', '.zeit.de']); 
        _gaq.push(['_gat._anonymizeIp']);
        _gaq.push(['_trackPageview']); 
        (function() { 
            var ga = document.createElement('script'); 
            ga.type = 'text/javascript'; 
            ga.async = true; 
            ga.src = ('https:' == document.location.protocol ? 'https://' : 'http://') + 'stats.g.doubleclick.net/dc.js';
            var s = document.getElementsByTagName('script')[0]; 
            s.parentNode.insertBefore(ga, s);
        })(); 
</script></div>
<!--end: tracker-->
```

## Webtrekk
### Fall 1: Startseite/Überblicksseite/Tag-Seite
Beispiel: http://marktplatz.zeit.de/urlaubsziele/
```html
<!-- Webtrekk 3.1.1, (c) www.webtrekk.com -->
<script type="text/javascript" src="http://scripts.zeit.de/static/js/webtrekk/webtrekk_v3.js"></script>
<script type="text/javascript">
    var webtrekk = {
        linkTrack : 'standard',
        heatmap : '0',
        linkTrackAttribute: 'id'
    };
    var wt = new webtrekkV3(webtrekk);
    // cookie handling
    wt.cookie = '1'; // (3|1, 1st or 3rd party cookie)
    wt.contentGroup = {
        1: 'verlag', // Zuordnung/Bereich
        2: 'centerpage', // Kategorie/Pagetype
        3: 'angebote', // Ressort
        4: 'online', // Online/Sourcetype
        5: 'urlaubsziele', // Subressort
        6: '', // Cluster
        7: 'marktplatz.zeit.de/urlaubsziele/', // URL                           
        8: '', // Banner-Channel
        9: '2014-10-29'
    };
    wt.contentId = 'verlag.angebote.urlaubsziele..centerpage.adv.marktplatz.zeit.de/urlaubsziele/'; // content id
    wt.sendinfo();
</script>
<noscript>
    <div>
        <img alt="" width="1" height="1" src="http://zeit01.webtrekk.net/981949533494636/wt.pl?p=311,verlag.angebote.urlaubsziele..centerpage.adv.marktplatz.zeit.de/urlaubsziele/,0,0,0,0,0,0,0,0&amp;cg1=verlag&amp;cg2=centerpage&amp;cg3=angebote&amp;cg4=online&amp;cg5=urlaubsziele&amp;cg6=&amp;cg7=marktplatz.zeit.de/urlaubsziele/&amp;cg8=zeit/homepage&amp;cg9=2014-10-29">
    </div>
</noscript>
```

### Fall 2: Artikelseiten (Anzeigen)
Beispiel: http://marktplatz.zeit.de/urlaubsziele/urlaubsarten/ligurian-hideaways/
```html
<!-- 
    Dies ist nur ein Beispiel, 
    der Code muss an den entsprechenden Stellen umgeschrieben werden,
    um die passenden Werte einzusetzen.
    (Diesen Kommentar entfernen.)
-->
<!-- Webtrekk 3.1.1, (c) www.webtrekk.com -->
<script type="text/javascript" src="http://scripts.zeit.de/static/js/webtrekk/webtrekk_v3.js"></script>
<script type="text/javascript">
    var webtrekk = {
        linkTrack : 'standard',
        heatmap : '0',
        linkTrackAttribute: 'id'
    };
    var wt = new webtrekkV3(webtrekk);
    // cookie handling
    wt.cookie = '1'; // (3|1, 1st or 3rd party cookie)
    wt.contentGroup = {
        1: 'verlag', // Zuordnung/Bereich
        2: 'artikel', // Kategorie/Pagetype
        3: 'angebote', // Ressort
        4: 'online', // Online/Sourcetype
        5: 'urlaubsziele', // Subressort
        6: '', // Cluster
        7: 'marktplatz.zeit.de/urlaubsziele/urlaubsarten/ligurian-hideaways/', // URL
        8: '', // Banner-Channel
        9: '2014-10-29'
    };
    wt.contentId = 'verlag.angebote.urlaubsziele..article.adv.marktplatz.zeit.de/urlaubsziele/urlaubsarten/ligurian-hideaways/'; // content id
    wt.sendinfo();
</script>
<!--
    Die Werte von oben werden im noscript-Bereich wiederholt.
    (Diesen Kommentar entfernen.)
-->
<noscript>
    <div>
        <img alt="" width="1" height="1" src="http://zeit01.webtrekk.net/981949533494636/wt.pl?p=311,verlag.angebote.urlaubsziele..article.adv.marktplatz.zeit.de/urlaubsziele/urlaubsarten/ligurian-hideaways/,0,0,0,0,0,0,0,0&amp;cg1=verlag&amp;cg2=artikel&amp;cg3=angebote&amp;cg4=online&amp;cg5=urlaubsziele&amp;cg6=&amp;cg7=marktplatz.zeit.de/urlaubsziele/urlaubsarten/ligurian-hideaways/&amp;cg8=&amp;cg9=2014-10-29">
    </div>
</noscript>
```

### Aktionsverpixelung mit Webtrekk

Alle Teaserklicks auf werbliche Outgoing-Links oder Anzeigenartikel, die gemessen werden sollen, müssen mit einer Aktionsverpixelung versehen werden.

Folgende grundsätzliche Logik muss in die <id> geschrieben werden:
[navigationstyp].[verortung].[reihe].[spalte].[subreihe].[bezeichner].[ZIEL-URL]

#### Beispiel 1
![Beispiel 1](/images/beispiel-1.png)

1. Klick auf das Bild des Teasers muss folgenden Call an Webtrekk auslösen:
`stationaer.teaserliste.1.links..image.marktplatz.zeit.de/urlaubsziele/beliebte-urlaubsziele/ein-ungewoehnliches-hotel-stadtrand-von-pristina/`
2. Klick auf die Überschrift des Teasers muss folgenden Call an Webtrekk auslösen:
`stationaer.teaserliste.1.links..headline.marktplatz.zeit.de/urlaubsziele/beliebte-urlaubsziele/ein-ungewoehnliches-hotel-stadtrand-von-pristina/`
3. Klick auf den “mehr”-Link des Teasers muss folgenden Call an Webtrekk auslösen:
`stationaer.teaserliste.1.links..more.marktplatz.zeit.de/urlaubsziele/beliebte-urlaubsziele/ein-ungewoehnliches-hotel-stadtrand-von-pristina/`

#### Beispiel 2
![Beispiel 2](/images/beispiel-2.png)

1. Klick auf das Bild des Teasers muss folgenden Call an Webtrekk auslösen:
`stationaer.neueste_angebote.1.rechts..image.marktplatz.zeit.de/urlaubsziele/urlaubsarten/von-der-loire-bis-zum-mekong/`
2. Klick auf die Überschrift des Teasers muss folgenden Call an Webtrekk auslösen:
`stationaer.neueste_angebote.1.rechts..headline.marktplatz.zeit.de/urlaubsziele/urlaubsarten/von-der-loire-bis-zum-mekong/`
3.Klick auf den “mehr”-Link des Teasers muss folgenden Call an Webtrekk auslösen:
`stationaer.neueste_angebote.1.rechts..more.marktplatz.zeit.de/urlaubsziele/urlaubsarten/von-der-loire-bis-zum-mekong/`
