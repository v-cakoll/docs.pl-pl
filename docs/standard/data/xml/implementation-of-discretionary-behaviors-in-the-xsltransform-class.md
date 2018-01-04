---
title: Implementacja DACL zachowania w klasie XslTransform
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2758ea1-03f6-47bd-88d2-0fb7ccdb2fab
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 98ad31039b5351a7dc4aa3cf033ae8cd0f896b7b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="implementation-of-discretionary-behaviors-in-the-xsltransform-class"></a>Implementacja DACL zachowania w klasie XslTransform
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [za pomocą klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [migracji z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 DACL zachowania są opisane zachowania wymienione w sieci World Wide Web konsorcjum W3C transformacji XSL (XSLT) wersji 1.0 zalecenie (www.w3.org/TR/xslt), w którym dostawca implementacji wybiera jeden z kilku możliwych opcji sposób do obsługi sytuacji. Na przykład w sekcji 7.3 Tworzenie przetwarzania instrukcje, zaleceń W3C mówi czy jest błąd, jeśli Tworzenie wystąpień zawartość `xsl:processing-instruction` tworzy węzły inne niż węzły tekstowe. W przypadku niektórych problemów W3C informuje decyzję, jakie należy wprowadzić Jeśli procesor decyduje o tym odzyskać sprawność po błędzie. Tego problemu podane w sekcji 7.3 W3C mówi, że implementacja można odzyskać tego błędu ignorowanie węzły i jego zawartość.  
  
 W związku z tym dla każdego DACL zachowania dozwolone przez konsorcjum W3C w poniższej tabeli przedstawiono zachowania DACL zaimplementowany dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementacja <xref:System.Xml.Xsl.XslTransform> klasy, a następnie co sekcji w zaleceń 1.0 XSLT W3C tego omówiono problem.  
  
|Problem|Zachowanie|Sekcja|  
|-------------|--------------|-------------|  
|Węzeł tekstowy jest zgodny zarówno `xsl:strip-space` i `xsl:preserve-space`.|Odzyskiwanie|3.4|  
|Węzeł źródłowy odpowiada więcej niż jeden szablon reguły.|Odzyskiwanie|5.5|  
|Identyfikator URI (Uniform Resource) przestrzeni nazw został zadeklarowany jako alias wielu URI przestrzeni nazw, wszystkie o tym samym ustawieniem pierwszeństwa importu.|Odzyskiwanie|7.1.1|  
|Atrybut nazwy w `xsl:attribute` i `xsl:element` generowane w szablonie wartości atrybutu nie jest prawidłową nazwą kwalifikowaną (QName).|Zgłoszono wyjątek|7.1.2 i 7.1.3|  
|Dodawanie atrybutu do elementu po węzły podrzędne już zostały dodane do węzła elementu.|Odzyskiwanie|7.1.3|  
|Dodawanie atrybutu na inny niż węzeł elementu.|Odzyskiwanie|7.1.3|  
|Podczas tworzenia wystąpienia zawartości `xsl:attribute` element nie jest węzłem tekstowym.|Odzyskiwanie|7.1.3|  
|Dwa zestawy atrybutu mają się tym samym ustawieniem pierwszeństwa importu i rozwiniętą nazwą. Mają taki sam atrybut i ma nie innych atrybutów zestaw, zawierający atrybutu wspólnego o takiej samej nazwie o wyższych ważności.|Odzyskiwanie|7.1.4|  
|`xsl:processing-instruction`Nazwa atrybutu nie przekazuje nazwę nie dwukropka (NCName) i elementem docelowym instrukcji przetwarzania.|Odzyskiwanie|7.3|  
|Tworzenie wystąpień zawartość `xsl:processing-instruction` tworzy węzły inne niż węzły tekstowe.|Odzyskiwanie|7.3|  
|Wyniki tworzenia wystąpienia zawartość `xsl:processing-instruction` zawiera ciąg "`?>`".|Odzyskiwanie|7.3|  
|Wyniki tworzenia wystąpienia zawartość `xsl:comment` zawiera ciąg "--", lub kończy się wyrazem "-".|Odzyskiwanie|7.4|  
|Wyniki tworzenia wystąpienia zawartość `xsl:comment` tworzy węzły inne niż węzły tekstowe.|Odzyskiwanie|7.4|  
|Szablon w elemencie powiązania zmiennej zwraca węzeł atrybutu lub przestrzeni nazw.|Odzyskiwanie|11.2|  
|Istnieje błąd podczas pobierania zasobu z identyfikatora URI przekazane do funkcji dokumentu.|Zgłoszono wyjątek|12.1|  
|Identyfikator fragmentu zawiera odwołanie do identyfikatora URI w dokumencie funkcji i występuje błąd podczas przetwarzania identyfikator fragmentu.|Zgłoszono wyjątek|12.1|  
|Wiele atrybutów o tej samej nazwie, które nie są nazywane `cdata-section-elements` w `xls:output`, a tym samym ustawieniem pierwszeństwa importu te atrybuty.|Odzyskiwanie|16|  
|Procesor nie obsługuje kodowania wartości podanej w znaków `encoding` atrybutu `xsl:output` elementu.|Odzyskiwanie|16.1|  
|`disable-output-escaping`Służy do węzłem tekstowym, a ten węzeł tekstowy jest używany do tworzenia inną niż węzeł tekstowy w drzewie wynik.|`disable-output-escaping`atrybut jest ignorowany|16.4|  
|Konwertowanie na liczbę lub ciąg wynikowego fragmentu drzewa, jeśli wynikowego fragmentu drzewa zawiera węzeł tekstowy z danych wyjściowych anulowanie włączone.|Ignorowane|16.4|  
|Anulowanie w danych wyjściowych jest wyłączona dla znaków, których nie można przedstawić w kodowaniu wykorzystanie procesora XSLT do danych wyjściowych.|Ignorowane|16.4|  
|Dodawanie węzła przestrzeni nazw do elementu po elementy podrzędne zostały dodane do niego lub atrybuty zostały dodane do niego|Odzyskiwanie|E25 erracie|  
|`xsl:number`jest wartością typu NaN, nieskończone lub mniejsza niż 0,5.|Odzyskiwanie|E24 erracie|  
|Drugi argument zestaw węzłów funkcji dokument jest pusty i odwołanie do identyfikatora URI jest względna|Odzyskiwanie|Erracie e14|  
  
 Sekcje z erracie znajdują się w sieci World Wide Web konsorcjum W3C transformacji XSL (XSLT) w wersji 1.0 specyfikacji erracie, znajdujący się w www.w3.org/1999/11/REC-xslt-19991116-errata.  
  
## <a name="custom-defined-implementation-behaviors"></a>Niestandardowy implementacji zachowania  
 Są unikatowe dla zachowania <xref:System.Xml.Xsl.XslTransform> implementację klasy. W tej sekcji omówiono implementacji specyficznych dla dostawcy `xsl:sort` i opcjonalne funkcje, które są obsługiwane przez <xref:System.Xml.Xsl.XslTransform> klasy.  
  
## <a name="xslsort"></a>sort  
 Podczas korzystania z transformacji do sortowania, zaleceń 1.0 XSLT W3C sprawia, że niektóre uwagi. Są to:  
  
-   Dwa procesory XSLT może być zgodne procesory, ale nadal może sortować inaczej.  
  
-   Nie wszystkie procesory XSLT obsługuje te same języki.  
  
-   W odniesieniu do języków, różnych procesorów może się różnić na ich sortowanie według określonego języka nie określono`xsl:sort.`  
  
 W poniższej tabeli przedstawiono sortowania zaimplementowana dla każdego typu danych w implementacji programu .NET Framework, przekształcania, używając <xref:System.Xml.Xsl.XslTransform>.  
  
|Typ danych|Zachowanie sortowania|  
|---------------|----------------------|  
|Tekst|Dane są sortowane przy użyciu wspólnej metody String.Compare środowiska uruchomieniowego (języka wspólnego CLR) języka i kultury ustawień regionalnych. Gdy jest równa "text" typ danych, sortowanie w <xref:System.Xml.Xsl.XslTransform> klasa działa tak samo zachowania porównanie ciągu środowiska CLR.|  
|Wartość liczbowa|Wartości numeryczne są traktowane jako liczby XML Path Language (XPath) i są sortowane według szczegóły opisane w wersji 1.0 W3C XML Path Language (XPath) zalecenia, sekcji 3.5 (www.w3.org/TR/xpath.html#numbers).|  
  
## <a name="optional-features-supported"></a>Obsługiwane funkcje opcjonalne  
 W poniższej tabeli przedstawiono funkcje, które są opcjonalne dla procesora XSLT do zaimplementowania i są implementowane w <xref:System.Xml.Xsl.XslTransform> klasy.  
  
|Funkcja|Odwołanie do lokalizacji|Uwagi|  
|-------------|------------------------|-----------|  
|`disable-output-escaping`atrybutu `<xsl:text...>` i `<xsl:value-of...>` tagów.|W3C XSLT 1.0 zalecenie,<br /><br /> 16.4 sekcji|`disable-output-escaping` Atrybut jest ignorowany podczas `xsl:text` lub `xsl:value-of` elementy są używane w `xsl:comment`, `xsl:processing-instruction`, lub `xsl:attribute` elementu.<br /><br /> Wynik drzewa fragmenty, zawierających tekst i tekst wyjściowy, który ma zostać zmieniona nie są obsługiwane.<br /><br /> Anulowanie dane wyjściowe wyłącz atrybut jest ignorowane w przypadku przekształcania do <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter> obiektu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Xsl.XslTransform>  
 [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [Klasa XPathNavigator w przekształceniach](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [Klasa XPathNodeIterator w przekształceniach](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Dane wejściowe obiektu XPathDocument klasy XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [Dane wejściowe obiektu XmlDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
