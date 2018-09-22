---
title: Odwracalne błędy XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 484929b0-fefb-4629-87ee-ebdde70ff1f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f7630b9a233db009b6095abc8d833870c1f33d8
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581937"
---
# <a name="recoverable-xslt-errors"></a>Odwracalne błędy XSLT
Zalecenie w wersji 1.0 W3C przekształcenia XSL (XSLT) obejmuje obszary, w których implementacja dostawcy może podjąć decyzję sposób obsługi sytuacji. Te obszary są uznawane za poufne zachowanie. Na przykład, w sekcji 7.3 tworzenia przetwarzania instrukcji, zalecenie specyfikacji XSLT 1.0 stwierdza, występuje błąd, jeśli utworzenie wystąpienia zawartość `xsl:processing-instruction` tworzy węzłów innych niż węzły tekstowe. Dla niektórych problemów specyfikacji XSLT 1.0 zalecenie wskazuje, jakie decyzją należy dokonać, jeśli procesor zdecyduje się odzyskać sprawność po błędzie. Ten problem, podane w sekcji 7.3 W3C mówi, że implementacja można odzyskać z tego błędu, ignorując węzły i ich zawartości.  
  
## <a name="discretionary-behaviors"></a>Zachowań uznaniowych  
 W poniższej tabeli wymieniono wszystkich zachowań uznaniowych dozwolone przez zalecenie specyfikacji XSLT 1.0 oraz jak te zachowania są obsługiwane przez <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
-   Odzyskaj wskazuje, że <xref:System.Xml.Xsl.XslCompiledTransform> klasy zostanie przywrócona do działania z tego błędu. <xref:System.Xml.Xsl.XsltArgumentList.XsltMessageEncountered?displayProperty=nameWithType> Zdarzeń może służyć do zgłaszania zdarzeń z procesora XSLT.  
  
-   Błąd wskazuje, czy wyjątek jest zgłaszany tego warunku.  
  
-   Odwołania do sekcji znajdują się w [W3C przekształcenia XSL (XSLT) w wersji 1.0 zalecenie](http://www.w3.org/TR/xslt) i [Errata specyfikacji wersji 1.0 W3C przekształcenia XSL (XSLT)](https://www.w3.org/1999/11/REC-xslt-19991116-errata/).  
  
|Warunek XSLT|Sekcja|Zachowanie XslCompiledTransform|  
|--------------------|-------------|-----------------------------------|  
|Węzeł tekstowy jest zgodny zarówno `xsl:strip-space` i `xsl:preserve-space`.|3.4|Odzyskiwanie|  
|Węzeł źródłowy odpowiada więcej niż jeden szablon reguły.|5.5|Odzyskiwanie|  
|Przestrzeń nazw identyfikatora URI jest zadeklarowany jako alias dla wielu URI przestrzeni nazw, wszystkie o ten sam priorytet importu.|7.1.1|Odzyskiwanie|  
|`name` Atrybutu w `xsl:attribute` i `xsl:element` wygenerowany na podstawie wartości atrybutu nie jest QName.|7.1.2, 7.1.3|Błąd *|  
|Atrybut dwa zestawy za pomocą tego samego importu i rozwinięta nazwa wspólnym atrybut nie jest inne atrybut zawierający wspólny atrybut o tej samej nazwie, o ważności wyższym.|7.1.4|Odzyskiwanie|  
|Dodawanie atrybutu do elementu, po elementy podrzędne zostały dodane do niego.|7.1.3|Błąd *|  
|Tworzenie atrybutu o nazwie "xmlns"|7.1.3|Błąd *|  
|Dodawanie atrybutu do węzła, który nie jest elementem.|7.1.3|Błąd *|  
|Tworzenie węzłów innych niż węzły tekstowe podczas tworzenia wystąpienia zawartości `xsl:attribute` atrybutu.|7.1.3|Błąd *|  
|`name` Atrybut `xsl:processing-instruction` nie przekazuje NCName i elementem docelowym instrukcji przetwarzania.|7.3|Błąd *|  
|Utworzenie wystąpienia zawartość `xsl:processing-instruction` tworzy węzłów innych niż węzły tekstowe.|7.3|Błąd *|  
|Wynik wystąpienia zawartość `xsl:processing-instruction` zawiera ciąg "? >"|7.3|Odzyskiwanie|  
|Wynik wystąpienia zawartość `xsl:processing-instruction` zawiera ciąg "--" lub kończy się ciągiem "-".|7.4|Odzyskiwanie|  
|Wynik wystąpienia zawartość `xsl:comment` tworzy węzłów innych niż węzły tekstowe.|7.4|Błąd *|  
|Szablon w obrębie elementu powiązania zmiennej zwraca węzeł atrybutu lub węzła obszaru nazw.|11.2|Błąd *|  
|Występuje błąd podczas pobierania zasobu z identyfikatora URI przekazywany do funkcji dokumentu.|12.1|Błąd|  
|Identyfikator URI odwołania do funkcji dokumentu zawiera identyfikator fragmentu i występuje błąd podczas przetwarzania identyfikator fragmentu.|12.1|Odzyskaj *|  
|Wiele atrybutów o tej samej nazwie, ale różnymi wartościami, nie są nazwane elementy sekcja cdata w `xsl:output` o takiej samej importowania pierwszeństwo.|16|Odzyskiwanie|  
|Procesor nie obsługuje kodowania w `xsl:output` atrybut kodowania.|16.1|Odzyskiwanie|  
|Wyłączanie danych wyjściowych anulowania zapewnianego element dla węzła tekstowego, który służy do coś innego niż węzeł tekstowy w drzewie wynik.|16.4|Odzyskaj *|  
|Konwertowanie wynikowego fragmentu drzewa liczbę lub ciąg, jeśli wynikowego fragmentu drzewa zawiera węzeł tekstowy z danych wyjściowych anulowania zapewnianego element włączone.|16.4|Odzyskaj *|  
|Anulowanie w danych wyjściowych jest wyłączone dla znak, który nie może być przedstawiony w kodowaniu, że procesora XSLT korzysta z danych wyjściowych.|16.4|Odzyskaj *|  
|Dodawanie węzła obszaru nazw do elementu, po dodaniu elementów podrzędnych do niego lub atrybuty zostały dodane do niego.|errata 25|Błąd *|  
|`value` Atrybutu `xsl:number` jest wartością typu NAN, nieskończoną lub mniejsze niż 0,5|errata 24|Odzyskiwanie|  
|Drugi argument zestaw węzłów funkcji dokument jest pusty i odwołanie do identyfikatora URI jest względny.|errata 14|Odzyskiwanie|  
  
 <sup>*</sup> To zachowanie jest inne niż w przypadku <xref:System.Xml.Xsl.XslTransform> klasy. Aby uzyskać więcej informacji, zobacz [implementacji zachowań uznaniowych w klasie XslTransform](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
