PPM-filter Widget – Inbäddningspaket
===================================

Detta paket innehåller en HTML-widget för att visa och filtrera PPM-fonder.
Filen är färdig att laddas upp till din hemsida (t.ex. i /assets/ eller motsvarande).

Filer:
- ppm-filter-widget.html   (själva widgeten)
- README.txt               (denna instruktion)

Så bäddar du in widgeten på din hemsida
---------------------------------------

1. Ladda upp `ppm-filter-widget.html` till din domän (t.ex. https://din-domän.se/assets/ppm-filter-widget.html).

2. Lägg in följande kod på den sida där du vill visa widgeten:

<div id="ppm-widget-wrap" style="width:100%;">
  <iframe
    id="ppm-widget"
    src="https://din-domän.se/assets/ppm-filter-widget.html"
    style="width:100%; border:0; overflow:hidden;"
    scrolling="no"
  ></iframe>
</div>

<script>
  (function () {
    var iframe = document.getElementById('ppm-widget');
    function setHeight(h){ if(iframe){ iframe.style.height = (h||600) + 'px'; } }
    setHeight(800); // fallback höjd

    window.addEventListener('message', function (e) {
      if (!e || !e.data) return;
      if (e.data.type === 'ppmWidgetHeight') {
        setHeight(e.data.height);
      }
    });
  })();
</script>

3. Publicera sidan. Widgeten laddas nu in från din uppladdade HTML-fil och autoanpassar höjden.

Tips
----
- Vill du ändra design (färger, typsnitt) kan du redigera css-delen i `ppm-filter-widget.html`.
- Widgeten fungerar i de flesta CMS som stödjer `<iframe>` (t.ex. WordPress, Hemsida24, Wix m.fl.).
- CSV-export och utskriftsfunktion fungerar även inbäddat.

Lycka till!
