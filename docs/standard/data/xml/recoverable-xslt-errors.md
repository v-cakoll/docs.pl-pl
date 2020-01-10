---
title: Odwracalne błędy XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 484929b0-fefb-4629-87ee-ebdde70ff1f8
ms.openlocfilehash: e3ff86cc80887d14fdffe50f256409cb70ff2d88
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710378"
---
# <a name="recoverable-xslt-errors"></a>Odwracalne błędy XSLT
Zalecenie dotyczące formatu W3C XSL Transformations (XSLT) w wersji 1,0 zawiera obszary, w których dostawca implementacji może zdecydować, jak obsługiwać sytuację. Te obszary są uważane za zachowanie uznaniowe. Na przykład, w sekcji 7,3 Tworzenie instrukcji przetwarzania, zalecenie XSLT 1,0 stwierdza, że występuje błąd, jeśli Tworzenie wystąpienia zawartości `xsl:processing-instruction` tworzy węzły inne niż węzły tekstowe. W przypadku niektórych problemów zalecenie XSLT 1,0 wskazuje, jakie decyzje należy podjąć, jeśli procesor zdecyduje się na odzyskanie po błędzie. W przypadku problemu podanym w sekcji 7,3 w tym przypadku W3C ma wpływ na to, że implementacja może zostać odzyskana po wystąpieniu tego błędu, ignorując węzły i ich zawartość.  
  
## <a name="discretionary-behaviors"></a>Zachowania własne  
 Poniższa tabela zawiera listę wszystkich zachowań uznania dozwolonych przez zalecenie XSLT 1,0 i sposób obsługi tych zachowań przez klasę <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
- Funkcja Recover wskazuje, że Klasa <xref:System.Xml.Xsl.XslCompiledTransform> odzyska z tego błędu. Zdarzenia <xref:System.Xml.Xsl.XsltArgumentList.XsltMessageEncountered?displayProperty=nameWithType> mogą służyć do raportowania wszelkich zdarzeń z procesora XSLT.  
  
- Błąd oznacza, że wyjątek jest wywoływany dla tego warunku.  
  
- Odwołania do sekcji znajdują się w [rekomendacji W3C XSL Transformations (XSLT) w wersji 1,0](https://www.w3.org/TR/xslt) i [formacie W3C XSL Transformations (XSLT) w wersji 1,0 Errata](https://www.w3.org/1999/11/REC-xslt-19991116-errata/).  
  
|Warunek XSLT|Sekcja|Zachowanie XslCompiledTransform|  
|--------------------|-------------|-----------------------------------|  
|Węzeł tekstowy pasuje do `xsl:strip-space` i `xsl:preserve-space`.|3.4|Odzyskaj|  
|Węzeł źródłowy jest zgodny z więcej niż jedną regułą szablonu.|5.5|Odzyskaj|  
|Identyfikator URI przestrzeni nazw jest zadeklarowany jako alias dla wielu identyfikatorów URI przestrzeni nazw, a wszystkie mają ten sam priorytet importu.|7.1.1|Odzyskaj|  
|Atrybut `name` w `xsl:attribute` i `xsl:element` generowany na podstawie wartości atrybutu nie jest QName.|7.1.2, 7.1.3|Porn|  
|Dwa zestawy atrybutów o tej samej imporcie i rozwiniętej nazwie mają wspólny atrybut i nie istnieje żaden inny zestaw atrybutów zawierający wspólny atrybut o tej samej nazwie o wyższym znaczeniu.|7.1.4|Odzyskaj|  
|Dodawanie atrybutu do elementu po dodaniu elementów podrzędnych do niego.|7.1.3|Porn|  
|Tworzenie atrybutu o nazwie "xmlns"|7.1.3|Porn|  
|Dodawanie atrybutu do węzła, który nie jest elementem.|7.1.3|Porn|  
|Tworzenie węzłów innych niż węzły tekstowe podczas tworzenia wystąpienia zawartości atrybutu `xsl:attribute`.|7.1.3|Porn|  
|Atrybut `name` `xsl:processing-instruction` nie zwraca elementu "NCName" i instrukcji przetwarzania.|7.3|Porn|  
|Tworzenie wystąpienia zawartości `xsl:processing-instruction` tworzy węzły inne niż węzły tekstowe.|7.3|Porn|  
|Wynik tworzenia wystąpienia zawartości `xsl:processing-instruction` zawiera ciąg "? >"|7.3|Odzyskaj|  
|Wynik tworzenia wystąpienia zawartości `xsl:processing-instruction` zawiera ciąg "--" lub kończący się znakiem "-".|7.4|Odzyskaj|  
|W wyniku wystąpienia zawartości `xsl:comment` tworzone są węzły inne niż węzły tekstowe.|7.4|Porn|  
|Szablon w elemencie powiązania zmiennej zwraca węzeł atrybutu lub węzeł przestrzeni nazw.|11.2|Porn|  
|Wystąpił błąd podczas pobierania zasobu z identyfikatora URI przesłanego do funkcji dokumentu.|12.1|Błąd|  
|Odwołanie do identyfikatora URI w funkcji dokumentu zawiera identyfikator fragmentu i występuje błąd podczas przetwarzania identyfikatora fragmentu.|12.1|Odtwarzania|  
|Istnieje wiele atrybutów o tej samej nazwie, ale różne wartości, które nie są nazwanymi elementami Section w `xsl:output` z tym samym ustawieniem pierwszeństwa importu.|16|Odzyskaj|  
|Procesor nie obsługuje kodowania w atrybucie kodowania `xsl:output`.|16.1|Odzyskaj|  
|Wyłączanie wyjścia ucieczki dla węzła tekstowego, który jest używany dla elementu innego niż węzeł tekstowy w drzewie wynik.|16.4|Odtwarzania|  
|Konwertowanie fragmentu drzewa wynikowego na liczbę lub ciąg, jeśli fragment drzewa wynik zawiera węzeł tekstowy z włączoną funkcją ucieczki wyjścia.|16.4|Odtwarzania|  
|Wyjście ucieczki jest wyłączone dla znaku, którego nie można reprezentować w kodowaniu używanym przez procesor XSLT do wyprowadzania danych wyjściowych.|16.4|Odtwarzania|  
|Dodanie węzła przestrzeni nazw do elementu po dodaniu elementów podrzędnych do niego lub po dodaniu do niego atrybutów.|errata 25|Porn|  
|`value` atrybut `xsl:number` ma wartość NAN, nieskończoność lub mniejszą niż 0,5|Errata 24|Odzyskaj|  
|Drugi argument jest ustawiony na funkcję dokumentu, a odwołanie do identyfikatora URI jest względne.|Errata 14|Odzyskaj|  
  
 <sup>*</sup> To zachowanie różni się od klasy <xref:System.Xml.Xsl.XslTransform>. Aby uzyskać więcej informacji, zobacz [implementacja zachowań uznaniowych w klasie XslTransform](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
