---
title: Odwracalne błędy XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 484929b0-fefb-4629-87ee-ebdde70ff1f8
ms.openlocfilehash: ada0b352cd867417ed3ecf86291df023ca7c579e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289099"
---
# <a name="recoverable-xslt-errors"></a>Odwracalne błędy XSLT
Zalecenie dotyczące formatu W3C XSL Transformations (XSLT) w wersji 1,0 zawiera obszary, w których dostawca implementacji może zdecydować, jak obsługiwać sytuację. Te obszary są uważane za zachowanie uznaniowe. Na przykład w sekcji 7,3 Tworzenie instrukcji przetwarzania, zalecenie XSLT 1,0 stwierdza, że występuje błąd w przypadku tworzenia wystąpienia zawartości `xsl:processing-instruction` tworzonych węzłów innych niż węzły tekstowe. W przypadku niektórych problemów zalecenie XSLT 1,0 wskazuje, jakie decyzje należy podjąć, jeśli procesor zdecyduje się na odzyskanie po błędzie. W przypadku problemu podanym w sekcji 7,3 w tym przypadku W3C ma wpływ na to, że implementacja może zostać odzyskana po wystąpieniu tego błędu, ignorując węzły i ich zawartość.  
  
## <a name="discretionary-behaviors"></a>Zachowania własne  
 Poniższa tabela zawiera listę wszystkich zachowań uznania dozwolonych przez zalecenie XSLT 1,0 i sposób obsługi tych zachowań przez <xref:System.Xml.Xsl.XslCompiledTransform> klasę.  
  
- Odzyskiwanie wskazuje, że <xref:System.Xml.Xsl.XslCompiledTransform> Klasa odzyska z tego błędu. <xref:System.Xml.Xsl.XsltArgumentList.XsltMessageEncountered?displayProperty=nameWithType>Zdarzenie może służyć do raportowania wszelkich zdarzeń z procesora XSLT.  
  
- Błąd oznacza, że wyjątek jest wywoływany dla tego warunku.  
  
- Odwołania do sekcji znajdują się w [rekomendacji W3C XSL Transformations (XSLT) w wersji 1,0](https://www.w3.org/TR/xslt) i [formacie W3C XSL Transformations (XSLT) w wersji 1,0 Errata](https://www.w3.org/1999/11/REC-xslt-19991116-errata/).  
  
|Warunek XSLT|Sekcja|Zachowanie XslCompiledTransform|  
|--------------------|-------------|-----------------------------------|  
|Węzeł tekstowy pasuje do obu `xsl:strip-space` i `xsl:preserve-space` .|3.4|Recover|  
|Węzeł źródłowy jest zgodny z więcej niż jedną regułą szablonu.|5,5|Recover|  
|Identyfikator URI przestrzeni nazw jest zadeklarowany jako alias dla wielu identyfikatorów URI przestrzeni nazw, a wszystkie mają ten sam priorytet importu.|ppkt|Recover|  
|`name`Atrybut w `xsl:attribute` i `xsl:element` wygenerowany na podstawie wartości atrybutu nie jest QName.|7.1.2, 7.1.3|Porn|  
|Dwa zestawy atrybutów o tej samej imporcie i rozwiniętej nazwie mają wspólny atrybut i nie istnieje żaden inny zestaw atrybutów zawierający wspólny atrybut o tej samej nazwie o wyższym znaczeniu.|7.1.4|Recover|  
|Dodawanie atrybutu do elementu po dodaniu elementów podrzędnych do niego.|7.1.3|Porn|  
|Tworzenie atrybutu o nazwie "xmlns"|7.1.3|Porn|  
|Dodawanie atrybutu do węzła, który nie jest elementem.|7.1.3|Porn|  
|Tworzenie węzłów innych niż węzły tekstowe podczas tworzenia wystąpienia zawartości `xsl:attribute` atrybutu.|7.1.3|Porn|  
|`name`Atrybut obiektu `xsl:processing-instruction` nie zwraca elementu "NCName" i instrukcji przetwarzania.|7.3|Porn|  
|Tworzenie wystąpienia zawartości `xsl:processing-instruction` tworzonych węzłów innych niż węzły tekstowe.|7.3|Porn|  
|Wynik tworzenia wystąpienia zawartości `xsl:processing-instruction` zawiera ciąg "? >"|7.3|Recover|  
|Wynik tworzenia wystąpienia zawartości `xsl:processing-instruction` zawiera ciąg "--" lub kończący się znakiem "-".|7.4|Recover|  
|Wynik tworzenia wystąpienia zawartości `xsl:comment` węzłów utworzonych poza węzłami tekstu.|7.4|Porn|  
|Szablon w elemencie powiązania zmiennej zwraca węzeł atrybutu lub węzeł przestrzeni nazw.|11,2|Porn|  
|Wystąpił błąd podczas pobierania zasobu z identyfikatora URI przesłanego do funkcji dokumentu.|12,1|Błąd|  
|Odwołanie do identyfikatora URI w funkcji dokumentu zawiera identyfikator fragmentu i występuje błąd podczas przetwarzania identyfikatora fragmentu.|12,1|Odtwarzania|  
|Istnieje wiele atrybutów o tej samej nazwie, ale różne wartości, które nie są nazwanymi elementami Section w ramach tego `xsl:output` samego pierwszeństwa importu.|16|Recover|  
|Procesor nie obsługuje kodowania w `xsl:output` atrybucie kodowania.|16,1|Recover|  
|Wyłączanie wyjścia ucieczki dla węzła tekstowego, który jest używany dla elementu innego niż węzeł tekstowy w drzewie wynik.|16,4|Odtwarzania|  
|Konwertowanie fragmentu drzewa wynikowego na liczbę lub ciąg, jeśli fragment drzewa wynik zawiera węzeł tekstowy z włączoną funkcją ucieczki wyjścia.|16,4|Odtwarzania|  
|Wyjście ucieczki jest wyłączone dla znaku, którego nie można reprezentować w kodowaniu używanym przez procesor XSLT do wyprowadzania danych wyjściowych.|16,4|Odtwarzania|  
|Dodanie węzła przestrzeni nazw do elementu po dodaniu elementów podrzędnych do niego lub po dodaniu do niego atrybutów.|Errata 25|Porn|  
|`value`Atrybut `xsl:number` jest NaN, nieskończony lub mniejszy niż 0,5|Errata 24|Recover|  
|Drugi argument jest ustawiony na funkcję dokumentu, a odwołanie do identyfikatora URI jest względne.|Errata 14|Recover|  
  
 <sup>*</sup>To zachowanie różni się od <xref:System.Xml.Xsl.XslTransform> klasy. Aby uzyskać więcej informacji, zobacz [implementacja zachowań uznaniowych w klasie XslTransform](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](xslt-transformations.md)
