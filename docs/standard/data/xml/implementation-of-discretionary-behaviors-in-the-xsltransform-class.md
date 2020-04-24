---
title: Implementowanie zachowań uznaniowych w klasie XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d2758ea1-03f6-47bd-88d2-0fb7ccdb2fab
ms.openlocfilehash: b37cb0f4bf9a85053d70d549ae005c7d50a50bc0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710807"
---
# <a name="implementation-of-discretionary-behaviors-in-the-xsltransform-class"></a>Implementowanie zachowań uznaniowych w klasie XslTransform

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w .NET Framework 2,0. Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md) .

Zachowania uznaniowe są opisane w zaleceniach wymienionych w artykule [organizacja World Wide Web Consortium (W3C) w wersji 1,0](https://www.w3.org/TR/1999/REC-xslt-19991116), w którym dostawca implementacji wybiera jedną z kilku możliwych opcji jako sposób obsługi sytuacji. Na przykład, w sekcji 7,3 tworzenia instrukcji przetwarzania, zalecenie W3C wskazuje, że występuje błąd w przypadku tworzenia wystąpienia zawartości `xsl:processing-instruction` tworzonych węzłów innych niż węzły tekstowe. W przypadku niektórych problemów konsorcjum W3C informuje, jakie decyzje należy podjąć, jeśli procesor zdecyduje się na odzyskanie po błędzie. W przypadku problemu podanym w sekcji 7,3 w tym przypadku W3C ma wpływ na to, że implementacja może zostać odzyskana po wystąpieniu tego błędu, ignorując węzły i ich zawartość.

W związku z tym w przypadku każdego z zachowań uznaniowych dozwolonych przez konsorcjum W3C w poniższej tabeli wymieniono zachowania uznaniowe zaimplementowane dla .NET Framework implementacji <xref:System.Xml.Xsl.XslTransform> klasy oraz informacje o tym, co znajduje się w sekcji w formacie W3C XSLT 1,0 zalecenia tego problemu.

|Problem|Zachowanie|Sekcja|
|-------------|--------------|-------------|
|Węzeł tekstowy pasuje do obu `xsl:strip-space` i `xsl:preserve-space`.|Recover|3.4|
|Węzeł źródłowy jest zgodny z więcej niż jedną regułą szablonu.|Recover|5,5|
|Przestrzeń nazw Uniform Resource Identifier (URI) jest zadeklarowana jako alias dla wielu identyfikatorów URI przestrzeni nazw, a wszystkie mają ten sam priorytet importu.|Recover|ppkt|
|Atrybut Name w `xsl:attribute` i `xsl:element` wygenerowany na podstawie szablonu wartości atrybutu nie jest prawidłową nazwą kwalifikowaną (QName).|Zgłoszono wyjątek|7.1.2 i 7.1.3|
|Dodawanie atrybutu do elementu po dodaniu węzłów podrzędnych do węzła elementu.|Recover|7.1.3|
|Dodawanie atrybutu do elementów innych niż węzeł elementu.|Recover|7.1.3|
|Tworzenie wystąpienia zawartości `xsl:attribute` elementu nie jest węzłem tekstowym.|Recover|7.1.3|
|Dwa zestawy atrybutów mają ten sam priorytet importu i rozwiniętą nazwę. Oba mają ten sam atrybut i nie istnieje żaden inny zestaw atrybutów zawierający wspólny atrybut o tej samej nazwie o wyższej ważności.|Recover|7.1.4|
|`xsl:processing-instruction`atrybut name nie zwraca nazwy (NCName) ani elementu docelowego instrukcji przetwarzania.|Recover|7.3|
|Tworzenie wystąpienia zawartości `xsl:processing-instruction` tworzonych węzłów innych niż węzły tekstowe.|Recover|7.3|
|Wyniki tworzenia wystąpienia zawartości `xsl:processing-instruction` zawiera ciąg "`?>`".|Recover|7.3|
|Wyniki tworzenia wystąpienia zawartości `xsl:comment` zawiera ciąg "--" lub kończące się znakiem "-".|Recover|7.4|
|Wyniki tworzenia wystąpienia zawartości węzłów `xsl:comment` utworzonych poza węzłami tekstowymi.|Recover|7.4|
|Szablon w elemencie powiązania zmiennej zwraca węzeł atrybutu lub węzeł przestrzeni nazw.|Recover|11,2|
|Wystąpił błąd podczas pobierania zasobu z identyfikatora URI przesłanego do funkcji dokumentu.|Zgłoszono wyjątek|12,1|
|Odwołanie do identyfikatora URI w funkcji dokumentu zawiera identyfikator fragmentu i występuje błąd podczas przetwarzania identyfikatora fragmentu.|Zgłoszono wyjątek|12,1|
|Istnieje wiele atrybutów o tej samej nazwie, które nie są nazwane `cdata-section-elements` w `xls:output`, i te atrybuty mają ten sam priorytet importu.|Recover|16|
|Procesor nie obsługuje wartości kodowania znaków podaną w `encoding` atrybucie `xsl:output` elementu.|Recover|16,1|
|`disable-output-escaping`jest używany dla węzła tekstowego, a ten węzeł tekstowy służy do tworzenia elementu innego niż węzeł tekstu w drzewie wynik.|`disable-output-escaping`atrybut jest ignorowany|16,4|
|Konwertowanie fragmentu drzewa wynikowego na liczbę lub ciąg, jeśli fragment drzewa wynik zawiera węzeł tekstowy z włączoną funkcją ucieczki wyjścia.|Ignorowane|16,4|
|Wyjściowe ucieczki jest wyłączone dla znaków, których nie można reprezentować w kodowaniu używanym przez procesor XSLT do wyprowadzania danych wyjściowych.|Ignorowane|16,4|
|Dodanie węzła przestrzeni nazw do elementu po dodaniu elementów podrzędnych do niego lub po dodaniu do niego atrybutów|Recover|Errata E25|
|`xsl:number`jest NaN, nieskończone lub mniejsze niż 0,5.|Recover|Errata E24|
|Drugi argument jest ustawiony na funkcję dokumentu, a odwołanie do identyfikatora URI jest względne|Recover|Errata E14|

Sekcje z errata można znaleźć w specyfikacji 1,0 w formacie W3C [XSL Transformations (XSLT)](https://www.w3.org/1999/11/REC-xslt-19991116-errata/).

## <a name="custom-defined-implementation-behaviors"></a>Niestandardowe zachowania implementacji

Istnieją zachowania unikatowe dla implementacji <xref:System.Xml.Xsl.XslTransform> klasy. W tej sekcji omówiono implementację implementacji `xsl:sort` i opcjonalnych funkcji, które są obsługiwane przez <xref:System.Xml.Xsl.XslTransform> klasę.

## <a name="xslsort"></a>sort

W przypadku korzystania z transformacji do sortowania w formacie W3C XSLT 1,0 zawarto pewne uwagi. Oto one:

- Dwa procesory XSLT mogą być zgodne z procesorami, ale nadal mogą być sortowane w różny sposób.

- Nie wszystkie procesory XSLT obsługują te same języki.

- W odniesieniu do języków różne procesory mogą się różnić w zależności od ich sortowania w określonym języku nieokreślonym w`xsl:sort.`

W poniższej tabeli przedstawiono zachowanie sortowania zaimplementowane dla każdego typu danych w .NET Framework implementacji transformacji przy użyciu <xref:System.Xml.Xsl.XslTransform>:

|Typ danych|Zachowanie sortowania|
|---------------|----------------------|
|Tekst|Dane są sortowane przy użyciu ciągu CLR (Common Language Runtime), metody Compare i kultur regionalnych. Gdy typ danych jest równy "text", sortowanie w <xref:System.Xml.Xsl.XslTransform> klasie zachowuje się identycznie z zachowaniem porównania ciągów dla środowiska CLR.|
|Liczba|Wartości liczbowe są traktowane jako numery języka ścieżki XML (XPath) i są sortowane zgodnie z szczegółowymi informacjami przedstawionymi w [temacie XML (W3C) Path Language (XPath) w wersji 1,0 zalecenia, sekcja 3,5](https://www.w3.org/TR/1999/REC-xpath-19991116/#numbers).|

## <a name="optional-features-supported"></a>Funkcje opcjonalne obsługiwane

W poniższej tabeli przedstawiono funkcje, które są opcjonalne dla procesora XSLT do implementacji i są zaimplementowane w <xref:System.Xml.Xsl.XslTransform> klasie.

|Funkcja|Lokalizacja odwołania|Uwagi|
|-------------|------------------------|-----------|
|`disable-output-escaping`atrybut `<xsl:text...>` i `<xsl:value-of...>` Tagi.|Zalecenie dotyczące W3C XSLT 1,0,<br /><br /> Sekcja 16,4|`disable-output-escaping` Atrybut `xsl:text` jest ignorowany `xsl:value-of` `xsl:comment`, gdy elementy lub są używane w elemencie, `xsl:processing-instruction`lub `xsl:attribute` .<br /><br /> Fragmenty drzewa wyników, które zawierają tekst i wyjście tekstu, które zostały zmienione, nie są obsługiwane.<br /><br /> Atrybut Disable-Output-ucieczki jest ignorowany podczas przekształcania na obiekt <xref:System.Xml.XmlReader> lub. <xref:System.Xml.XmlWriter>|

## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Xsl.XslTransform>
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](xsltransform-class-implements-the-xslt-processor.md)
- [Przekształcenia XSLT przy użyciu klasy XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [Klasa XPathNavigator w przekształceniach](xpathnavigator-in-transformations.md)
- [Klasa XPathNodeIterator w przekształceniach](xpathnodeiterator-in-transformations.md)
- [Dane wejściowe obiektu XPathDocument klasy XslTransform](xpathdocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](xmldatadocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDocument klasy XslTransform](xmldocument-input-to-xsltransform.md)
