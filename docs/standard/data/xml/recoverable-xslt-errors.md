---
title: Błędy możliwe do odzyskania XSLT
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 484929b0-fefb-4629-87ee-ebdde70ff1f8
caps.latest.revision: 2
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 70491e86697356766b64a98201b2969883ab7ee4
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="recoverable-xslt-errors"></a>Błędy możliwe do odzyskania XSLT
Zalecenia w wersji 1.0 W3C transformacji XSL (XSLT) obejmuje obszary, w których implementacji dostawcy może decyzję dotyczącą sposobu obsługi sytuacji. Te obszary są uważane za DACL zachowanie. Na przykład w sekcji 7.3 Tworzenie przetwarzania instrukcje, zalecenie XSLT 1.0 stwierdza, czy jest błąd, jeśli Tworzenie wystąpień zawartość `xsl:processing-instruction` tworzy węzły inne niż węzły tekstowe. W przypadku niektórych problemów 1.0 XSLT zalecenie wskazuje co decyzja należy Jeśli procesor decyduje o tym odzyskać sprawność po błędzie. Tego problemu podane w sekcji 7.3 W3C mówi, że implementacja można odzyskać tego błędu ignorowanie węzły i jego zawartość.  
  
## <a name="discretionary-behaviors"></a>DACL zachowania  
 Poniższa tabela zawiera listę DACL zachowania dozwoloną zalecenie XSLT 1.0 i sposób obsługi tych zachowań przez <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
-   Odzyskaj wskazuje, że <xref:System.Xml.Xsl.XslCompiledTransform> klasy odzyska tego błędu. <xref:System.Xml.Xsl.XsltArgumentList.XsltMessageEncountered?displayProperty=nameWithType> Zdarzeń może służyć do zgłaszania zdarzeń z procesorze XSLT.  
  
-   Błąd wskazuje, czy wyjątek jest zgłaszany tego warunku.  
  
-   Można znaleźć w sekcji odwołań [W3C transformacji XSL (XSLT) w wersji 1.0 zalecenie](http://www.w3.org/TR/xslt) i [W3C transformacji XSL (XSLT) w wersji 1.0 specyfikacji erracie](https://www.w3.org/1999/11/REC-xslt-19991116-errata/).  
  
|Warunek XSLT|Sekcja|Zachowanie XslCompiledTransform|  
|--------------------|-------------|-----------------------------------|  
|Węzeł tekstowy jest zgodny zarówno `xsl:strip-space` i `xsl:preserve-space`.|3.4|Odzyskiwanie|  
|Węzeł źródłowy odpowiada więcej niż jeden szablon reguły.|5.5|Odzyskiwanie|  
|Przestrzeń nazw identyfikatora URI został zadeklarowany jako alias wielu URI przestrzeni nazw, wszystkie o tym samym ustawieniem pierwszeństwa importu.|7.1.1|Odzyskiwanie|  
|`name` Atrybutu w `xsl:attribute` i `xsl:element` generowane na podstawie wartości atrybutu nie jest QName.|7.1.2, 7.1.3|Błąd *|  
|Atrybut dwa zestawy za pomocą tego samego importu i rozwinięta nazwa atrybutu mają wspólną i nie ma nie zawierające atrybutu wspólnego o tej samej nazwie i z wyższej znaczenie innych zestawu atrybutów.|7.1.4|Odzyskiwanie|  
|Po dodaniu elementów podrzędnych do niego, dodając atrybut do elementu.|7.1.3|Błąd *|  
|Tworzenie atrybut o nazwie "xmlns"|7.1.3|Błąd *|  
|Dodawanie atrybutu do węzła, który nie jest elementem.|7.1.3|Błąd *|  
|Tworzenie węzły inne niż węzły tekstowe podczas tworzenia wystąpienia elementu zawartości `xsl:attribute` atrybutu.|7.1.3|Błąd *|  
|`name` Atrybut `xsl:processing-instruction` nie przekazuje zarówno NCName i elementem docelowym instrukcji przetwarzania.|7.3|Błąd *|  
|Tworzenie wystąpień zawartość `xsl:processing-instruction` tworzy węzły inne niż węzły tekstowe.|7.3|Błąd *|  
|Wynik uruchamianiu zawartość `xsl:processing-instruction` zawiera ciąg "? >"|7.3|Odzyskiwanie|  
|Wynik uruchamianiu zawartość `xsl:processing-instruction` zawiera ciąg "--" lub kończy się wyrazem "-".|7.4|Odzyskiwanie|  
|Wynik uruchamianiu zawartość `xsl:comment` tworzy węzły inne niż węzły tekstowe.|7.4|Błąd *|  
|Szablon w elemencie powiązania zmiennej zwraca węzeł atrybutu lub przestrzeni nazw.|11.2|Błąd *|  
|Istnieje błąd podczas pobierania zasobu z identyfikatora URI przekazane do funkcji dokumentu.|12.1|Błąd|  
|Identyfikator fragmentu zawiera odwołanie do identyfikatora URI w funkcji dokumentu i występuje błąd podczas przetwarzania identyfikator fragmentu.|12.1|Odzyskaj *|  
|Wiele atrybutów o tej samej nazwy, ale różne wartości, nie zostaną nazwane elementy sekcji cdata `xsl:output` o takim samym zaimportować pierwszeństwo.|16|Odzyskiwanie|  
|Procesor nie obsługuje kodowania w `xsl:output` atrybut kodowania.|16.1|Odzyskiwanie|  
|Wyłączanie danych wyjściowych anulowanie węzła tekstu, który jest używany do czegoś innego niż węzłem tekstowym w drzewie wynik.|16.4|Odzyskaj *|  
|Konwertowanie na liczbę lub ciąg wynikowego fragmentu drzewa, jeśli wynikowego fragmentu drzewa zawiera węzeł tekstowy z danych wyjściowych anulowanie włączone.|16.4|Odzyskaj *|  
|Anulowanie w danych wyjściowych jest wyłączona dla znaku, który nie może być reprezentowany w kodowaniu wykorzystanie procesora XSLT do danych wyjściowych.|16.4|Odzyskaj *|  
|Dodawanie węzła przestrzeni nazw do elementu po elementy podrzędne zostały dodane do niego lub atrybuty zostały dodane do niego.|erracie 25|Błąd *|  
|`value` Atrybutu `xsl:number` jest wartością typu NAN, nieskończone lub mniejsza niż 0,5|erracie 24|Odzyskiwanie|  
|Drugi argument zestaw węzłów funkcji dokument jest pusty i odwołanie do identyfikatora URI jest względny.|erracie 14|Odzyskiwanie|  
  
 <sup>*</sup> To zachowanie różni się od elementu <xref:System.Xml.Xsl.XslTransform> klasy. Aby uzyskać więcej informacji, zobacz [implementacji zachowania DACL w klasie XslTransform](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
