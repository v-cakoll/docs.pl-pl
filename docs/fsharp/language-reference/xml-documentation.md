---
title: Dokumentacja XML (F#)
description: 'Dowiedz się więcej o pomocy technicznej w języku F # do generowania dokumentacji z komentarzy.'
ms.date: 05/16/2016
ms.openlocfilehash: 1a4cb132e65b630821e5eb2b39276c1de99aff80
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45641628"
---
# <a name="xml-documentation"></a>Dokumentacja XML

Dokumentacja z trzema ukośnikami (/ / /) służy do tworzenia kodu komentarzy w języku F #. Komentarze XML może znajdować się przed deklaracjami w kodu pliki (.fs) lub podpisu (.fsi).

## <a name="generating-documentation-from-comments"></a>Generowanie komentarzy dokumentacji

Obsługa języka F # Generowanie komentarzy dokumentacji jest taka sama jak w innych językach .NET Framework. Tak jak w innych językach .NET Framework [-doc — opcja kompilatora](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) pozwala wygenerować plik XML, który zawiera informacje, które można przekształcić w dokumentacji, za pomocą narzędzia takiego jak Sandcastle. Dokumentacja, wygenerowane za pomocą narzędzia, które są przeznaczone do użytku z zestawów, które są zwykle zapisywane w innych językach .NET Framework generuje widok interfejsów API, które opiera się na formularzu skompilowane konstrukcje F #. Chyba, że narzędzia przeznaczone do obsługi F #, dokumentacji, generowanych przez te narzędzia jest niezgodna widoku F # interfejsu API.

Aby uzyskać więcej informacji na temat generowania dokumentacji z pliku XML, zobacz [komentarze dokumentacji XML &#40;C&#35; Programming Guide&#41;](https://msdn.microsoft.com/library/b2s063f7).

## <a name="recommended-tags"></a>Zalecane tagi

Istnieją dwa sposoby, aby zapisać komentarze dokumentacji XML. Jeden to wystarczy napisać dokumentację bezpośrednio w komentarzu potrójnym ukośnikiem, bez użycia tagów XML. Jeśli to zrobisz, cały tekst jest traktowana jako podsumowania dokumentacji konstrukcję kodu, który poprzedza. Użyj tej metody, gdy chcesz napisać tylko krótkie podsumowanie każdego konstrukcji. Inna metoda jest udostępnić więcej dokumentacji ze strukturą za pomocą tagów XML. Druga metoda, można określić oddzielne informacje o krótkie podsumowanie, dodatkowe uwagi, dokumentacji dla każdego parametru, parametr typu i wyjątki zgłaszane i opis wartości zwracanej. W poniższej tabeli opisano tagi XML, które są rozpoznawane w komentarzach do kodu XML F #.

|Składnia znacznika|Opis|
|----------|-----------|
|**&lt;c&gt;***tekstu***&lt;/c&gt;**|Określa, że *tekstu* jest kod. Ten tag może służyć przez generatory dokumentacji do wyświetlania tekstu w czcionkę, która jest odpowiednia dla kodu.|
|**&lt;Podsumowanie&gt;***tekstu*** &lt; /summary&gt;**|Określa, że *tekstu* znajduje się krótki opis elementu programu. Długość opisu jest zwykle jeden lub dwa zdania.|
|**&lt;Uwagi&gt;***tekstu*** &lt; /remarks&gt;**|Określa, że *tekstu* zawiera dodatkowe informacje o elemencie programu.|
|**&lt;param name = "***nazwa***"&gt;***opis***&lt;/param&gt;**|Określa nazwę i opis parametru funkcji lub metody.|
|**&lt;typeparam name = "***nazwa***"&gt;***opis***&lt;/typeparam&gt;**|Określa nazwę i opis dla parametru typu.|
|**&lt;Zwraca&gt;***tekstu*** &lt; /returns&gt;**|Określa, że *tekstu* opisuje wartość zwracaną funkcji lub metody.|
|**&lt;wyjątek cref = "***typu***"&gt;***opis***&lt;/exception&gt;**|Określa typ wyjątku, który może zostać wygenerowany i okoliczności, w których jest generowany.|
|**&lt;patrz cref = "***odwołania***"&gt;***tekstu*** &lt; /see&gt;**|Określa wbudowany link prowadzący do innego elementu programu. *Odwołania* to nazwa, która jest wyświetlana w pliku dokumentacji XML. *Tekstu* jest tekst wyświetlany w linku.|
|**&lt;SeeAlso — cref = "***odwołania***" /&gt;**|Określa, zobacz też link do dokumentacji dla innego typu. *Odwołania* to nazwa, która jest wyświetlana w pliku dokumentacji XML. Zobacz też linki, które zwykle są wyświetlane w dolnej części strony dokumentacji.|
|**&lt;para&gt;***tekstu***&lt;/para&gt;**|Określa akapit tekstu. To jest używany do oddzielania tekst wewnątrz **uwagi** tagu.|

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniżej przedstawiono typowe komentarzu dokumentacji XML w pliku podpisu.

### <a name="code"></a>Kod

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy kod przedstawia alternatywną metodą, bez znaczników XML. W tym przykładzie podsumowanie jest uważany za cały tekst w komentarzu. Należy pamiętać, że jeśli nie zostanie jawnie summary — tag, nie należy określać innych tagów, takich jak **param** lub **zwraca** tagów.

### <a name="code"></a>Kod

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Opcje kompilatora](compiler-options.md)
