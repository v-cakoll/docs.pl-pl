---
title: Dokumentacja XML (F#)
description: 'Informacje o pomocy technicznej w języku F # generowania dokumentacji z komentarzy.'
ms.date: 05/16/2016
ms.openlocfilehash: 8bdea89ac810851af07d3aedbbb17d5d90a92ff8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xml-documentation"></a>Dokumentacja XML

Dokumentacja z triple ukośnika (/ / /) można utworzyć kod komentarzy w języku F #. Komentarze XML może znajdować się przed deklaracjami w plikach kodu (.fs) lub pliki sygnatur (.fsi).


## <a name="generating-documentation-from-comments"></a>Generowanie dokumentacji z komentarzy
Obsługa w języku F # Generowanie dokumentacji z komentarzy jest takie samo jak w innych językach .NET Framework. Jak w innych językach .NET Framework [-doc — opcja kompilatora](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) pozwala utworzyć plik XML, który zawiera informacje, które można przekształcić w dokumentacji przy użyciu narzędzia, takiego jak Sandcastle. Dokumentacja wygenerowanych przy użyciu narzędzia, które są przeznaczone do użytku z zestawów, które są zwykle zapisywane w innych językach .NET Framework utworzyć widok interfejsów API, które jest oparta na formularzu skompilowanych konstrukcji F #. O ile w szczególności obsługi narzędzi F #, dokumentacji generowane przez te narzędzia pasuje do widoku F # interfejsu API.

Aby uzyskać więcej informacji na temat generowania dokumentacji z pliku XML, zobacz [komentarze dokumentacji XML &#40;C&#35; przewodnik programowania w języku&#41;](https://msdn.microsoft.com/library/b2s063f7).


## <a name="recommended-tags"></a>Zalecane tagi
Istnieją dwa sposoby zapisu komentarze dokumentacji XML. Jeden jest tylko zapisu w dokumentacji bezpośrednio w komentarzu potrójnym ukośnikiem, bez użycia tagów XML. Jeśli to zrobisz, cały tekst jest traktowana jako podsumowania dokumentację konstrukcję kodu, który bezpośrednio. Użyj tej metody, jeśli chcesz zapisać krótkie podsumowanie dla każdego konstrukcji. Inne metody jest dokumentacja więcej strukturalnych za pomocą tagów XML. Druga metoda umożliwia określenie oddzielne informacje o krótkie podsumowanie, uwagi dodatkowe dokumentacji dla każdego parametru i parametr typu i wyjątki zgłaszane i opis zwracanej wartości. W poniższej tabeli opisano tagi XML, które są rozpoznawane w komentarze w kodzie XML F #.



|Składnia znacznika|Opis|
|----------|-----------|
|**&lt;c&gt;***tekst***&lt;/c&gt;**|Określa, że *tekst* jest kod. Ten tag mogą posłużyć generatory dokumentacji do wyświetlania tekstu w czcionki, który jest odpowiedni dla kodu.|
|**&lt;Podsumowanie&gt;***tekst*** &lt; /summary&gt;**|Określa, że *tekst* znajduje się krótki opis elementu programu. Opis jest zwykle jeden lub dwa zdania.|
|**&lt;Uwagi&gt;***tekst*** &lt; /uwagi&gt;**|Określa, że *tekst* zawiera dodatkowe informacje dotyczące elementu programu.|
|**&lt;param name = "***nazwa***"&gt;***opis***&lt;/param&gt;**|Określa nazwę i opis dla parametru metody lub funkcji.|
|**&lt;typeparam name = "***nazwa***"&gt;***opis***&lt;/typeparam&gt;**|Określa nazwę i opis dla parametru typu.|
|**&lt;Zwraca&gt;***tekst*** &lt; /zwraca&gt;**|Określa, że *tekst* opisuje wartość zwracaną metody lub funkcji.|
|**&lt;wyjątek cref = "***typu***"&gt;***opis***&lt;/exception&gt;**|Określa typ wyjątku, który można wygenerować oraz okoliczności, w których jest generowany.|
|**&lt;patrz cref = "***odwołania***"&gt;***tekst*** &lt; /zobacz&gt;**|Określa wbudowany link do innego elementu programu. *Odwołania* to nazwa, która jest wyświetlana w pliku dokumentacji XML. *Tekst* jest tekst wyświetlany w łączu.|
|**&lt;SeeAlso cref = "***odwołania***" /&gt;**|Określa łącze Zobacz też w dokumentacji innego typu. *Odwołania* to nazwa, która jest wyświetlana w pliku dokumentacji XML. Zobacz też łącza są zwykle widoczne w dolnej części strony dokumentacji.|
|**&lt;para&gt;***tekst***&lt;/para&gt;**|Określa akapit tekstu. Służy do oddzielania tekst wewnątrz **uwagi** tagu.|

## <a name="example"></a>Przykład

### <a name="description"></a>Opis
Poniżej przedstawiono typowe komentarz dokumentacji XML w pliku podpisu.


### <a name="code"></a>Kod
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]
    
## <a name="example"></a>Przykład

### <a name="description"></a>Opis
Poniższy przykład przedstawia alternatywną metodą, bez tagów XML. W tym przykładzie podsumowanie jest uważany za cały tekst w komentarzu. Należy pamiętać, że jeśli nie zostanie jawnie podsumowania znacznika, nie należy określać innych tagów, takich jak **param** lub **zwraca** tagów.


### <a name="code"></a>Kod
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]
    
## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Opcje kompilatora](compiler-options.md)
