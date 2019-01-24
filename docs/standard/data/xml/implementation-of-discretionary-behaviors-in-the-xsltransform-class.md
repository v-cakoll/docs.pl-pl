---
title: Implementowanie zachowań uznaniowych w klasie XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d2758ea1-03f6-47bd-88d2-0fb7ccdb2fab
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1602479d4986109ffe89a87250297ee5687930ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609580"
---
# <a name="implementation-of-discretionary-behaviors-in-the-xsltransform-class"></a>Implementowanie zachowań uznaniowych w klasie XslTransform

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Klasy jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [używanie klasy XslCompiledTransform](using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.

Zachowań uznaniowych są określane jako zachowań na liście [World Wide Web Consortium (W3C) przekształcenia XSL (XSLT) w wersji 1.0 zalecenie](https://www.w3.org/TR/1999/REC-xslt-19991116), w której dostawcy implementacja wybiera, jeden z kilku możliwych Opcje jako sposób obsługi sytuacji. Na przykład w sekcji 7.3 tworzenia przetwarzania instrukcji, W3C zalecenie jest wyświetlany komunikat, występuje błąd, jeśli utworzenie wystąpienia zawartość `xsl:processing-instruction` tworzy węzłów innych niż węzły tekstowe. Dla niektórych problemów W3C informuje, jakie decyzja powinna zostać podjęta przez procesor postanawia odzyskać sprawność po błędzie. Ten problem, podane w sekcji 7.3 W3C mówi, że implementacja można odzyskać z tego błędu, ignorując węzły i ich zawartości.

W związku z tym, dla wszystkich zachowań uznaniowych dozwolone przez konsorcjum W3C w poniższej tabeli wymieniono zachowań uznaniowych zaimplementowane dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementacji <xref:System.Xml.Xsl.XslTransform> klasy i co sekcji zalecenia 1.0 W3C XSLT że omówiono problem.

|Problem|Zachowanie|Sekcja|
|-------------|--------------|-------------|
|Węzeł tekstowy jest zgodny zarówno `xsl:strip-space` i `xsl:preserve-space`.|Odzyskiwanie|3.4|
|Węzeł źródłowy odpowiada więcej niż jeden szablon reguły.|Odzyskiwanie|5.5|
|Przestrzeń nazw identyfikator (URI) jest zadeklarowany jako alias dla wielu przestrzeniach nazw identyfikatorów URI wszystkie o ten sam priorytet importu.|Odzyskiwanie|7.1.1|
|Atrybut nazwy w `xsl:attribute` i `xsl:element` wygenerowany na podstawie szablon wartość atrybutu nie jest prawidłowy, kwalifikowana nazwa (QName).|Zgłoszono wyjątek|7.1.2 i 7.1.3|
|Dodawanie atrybutu do elementu, po węzły podrzędne zostały już dodane do węzła elementu.|Odzyskiwanie|7.1.3|
|Dodawanie atrybutu do coś innego niż węzeł elementu.|Odzyskiwanie|7.1.3|
|Podczas tworzenia wystąpienia zawartości `xsl:attribute` element nie jest węzłem tekstowym.|Odzyskiwanie|7.1.3|
|Dwóch zestawów atrybutów, mają ten sam priorytet importu i rozwiniętej nazwy. Mają tego samego atrybutu, a ustawiono atrybut nie, zawierający wspólny atrybut o tej samej nazwie, o ważności wyższym.|Odzyskiwanie|7.1.4|
|`xsl:processing-instruction` Atrybut nazwy nie przekazuje zarówno nazwę nie dwukropka (NCName), jak i docelowym instrukcji przetwarzania.|Odzyskiwanie|7.3|
|Utworzenie wystąpienia zawartość `xsl:processing-instruction` tworzy węzłów innych niż węzły tekstowe.|Odzyskiwanie|7.3|
|Wyniki wystąpienia zawartość `xsl:processing-instruction` zawiera ciąg "`?>`".|Odzyskiwanie|7.3|
|Wyniki wystąpienia zawartość `xsl:comment` zawiera ciąg "--", lub kończy się ciągiem "-".|Odzyskiwanie|7.4|
|Wyniki wystąpienia zawartość `xsl:comment` tworzy węzłów innych niż węzły tekstowe.|Odzyskiwanie|7.4|
|Szablon w obrębie elementu powiązania zmiennej zwraca węzeł atrybutu lub węzła obszaru nazw.|Odzyskiwanie|11.2|
|Występuje błąd podczas pobierania zasobu z identyfikatora URI przekazywany do funkcji dokumentu.|Zgłoszono wyjątek|12.1|
|Identyfikator URI odwołania do funkcji dokumentu zawiera identyfikator fragmentu i występuje błąd podczas przetwarzania identyfikator fragmentu.|Zgłoszono wyjątek|12.1|
|Wiele atrybutów o tej samej nazwie, które nie są nazwane `cdata-section-elements` w `xls:output`, a te atrybuty mają ten sam priorytet importu.|Odzyskiwanie|16|
|Procesor nie obsługuje kodowania wartości podanej w znaków `encoding` atrybutu `xsl:output` elementu.|Odzyskiwanie|16.1|
|`disable-output-escaping` Służy do węzła tekstowego, a ten węzeł tekstowy jest używany do tworzenia coś innego niż węzeł tekstowy w drzewie wynik.|`disable-output-escaping` atrybut jest ignorowany|16.4|
|Konwertowanie wynikowego fragmentu drzewa liczbę lub ciąg, jeśli wynikowego fragmentu drzewa zawiera węzeł tekstowy z danych wyjściowych anulowania zapewnianego element włączone.|Ignorowane|16.4|
|Anulowanie w danych wyjściowych jest wyłączone dla znaków, których nie można przedstawić w kodowaniu, że procesora XSLT korzysta z danych wyjściowych.|Ignorowane|16.4|
|Dodawanie węzła obszaru nazw do elementu, po dodaniu elementów podrzędnych do niego lub atrybuty zostały dodane do niego|Odzyskiwanie|Errata e25|
|`xsl:number` jest wartością typu NaN, nieskończoną lub mniejsze niż 0,5.|Odzyskiwanie|Errata e24|
|Drugi argument zestaw węzłów funkcji dokument jest pusty i odwołanie do identyfikatora URI jest względna|Odzyskiwanie|Errata e14|

Sekcje z errata znajdują się w W3C [przekształcenia XSL (XSLT) w wersji 1.0 specyfikacji Errata](https://www.w3.org/1999/11/REC-xslt-19991116-errata/).

## <a name="custom-defined-implementation-behaviors"></a>Niestandardowy do implementacji zachowania

Są unikatowe dla zachowania <xref:System.Xml.Xsl.XslTransform> Implementacja klasy. W tej sekcji omówiono wykonania właściwe dla dostawcy `xsl:sort` i opcjonalne funkcje, które są obsługiwane przez <xref:System.Xml.Xsl.XslTransform> klasy.

## <a name="xslsort"></a>sort

Sortowanie za pomocą transformacji, zalecenia 1.0 W3C XSLT sprawia, że niektóre uwagi. Są to:

- Dwa procesory XSLT procesorów może być zgodne, ale nadal może być sortowane w inny sposób.

- Nie wszystkie procesory w systemie XSLT obsługują te same języki.

- Języki, w odniesieniu do różnych procesorów mogą być różne od ich sortowanie dla danego języka nie określono `xsl:sort.`

W poniższej tabeli przedstawiono sortowania zaimplementowane dla każdego typu danych w implementacji .NET Framework przy użyciu transformacji <xref:System.Xml.Xsl.XslTransform>:

|Typ danych|Zachowanie sortowania|
|---------------|----------------------|
|Tekst|Dane są sortowane przy użyciu wspólnego języka wspólnego (CLR) String.COMPARE — metoda i kultury ustawień regionalnych. Gdy jest równa "text" typ danych, sortowanie w <xref:System.Xml.Xsl.XslTransform> klasy działa identycznie do zachowania porównania ciągu środowiska CLR.|
|Wartość liczbowa|Wartości liczbowe są traktowane jako liczby XML Path Language (XPath) i są sortowane zgodnie ze szczegółami przedstawione W3C [XML Path Language (XPath) w wersji 1.0 zalecenie, sekcja 3.5](https://www.w3.org/TR/1999/REC-xpath-19991116/#numbers).|

## <a name="optional-features-supported"></a>Obsługiwane funkcje opcjonalne

W poniższej tabeli przedstawiono funkcje, które są opcjonalne dla procesora XSLT można wdrożyć i są implementowane w <xref:System.Xml.Xsl.XslTransform> klasy.

|Funkcja|Odwołanie do lokalizacji|Uwagi|
|-------------|------------------------|-----------|
|`disable-output-escaping` atrybutu na `<xsl:text...>` i `<xsl:value-of...>` tagów.|W3C XSLT 1.0 zalecenia<br /><br /> Sekcja 16.4|`disable-output-escaping` Atrybut jest ignorowany w przypadku `xsl:text` lub `xsl:value-of` elementy są używane w `xsl:comment`, `xsl:processing-instruction`, lub `xsl:attribute` elementu.<br /><br /> Fragmenty drzewa wynik, które zawierają tekst i tekstu wyjściowego, który ma zostać zmieniona, nie są obsługiwane.<br /><br /> Anulowanie dane wyjściowe wyłącz atrybut jest ignorowany w przypadku przekształcania w <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter> obiektu.|

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Xsl.XslTransform>
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](xsltransform-class-implements-the-xslt-processor.md)
- [Przekształcenia XSLT przy użyciu klasy XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [Klasa XPathNavigator w przekształceniach](xpathnavigator-in-transformations.md)
- [Klasa XPathNodeIterator w przekształceniach](xpathnodeiterator-in-transformations.md)
- [Dane wejściowe obiektu XPathDocument klasy XslTransform](xpathdocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](xmldatadocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDocument klasy XslTransform](xmldocument-input-to-xsltransform.md)
