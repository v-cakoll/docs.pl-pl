---
title: Dokumentacja XML (F#)
description: Dowiedz się więcej o obsłudze w F# generowania dokumentacji z komentarzy.
ms.date: 05/16/2016
ms.openlocfilehash: a1fb5eb682ff1188136b31b64e2d7c537d2c9a0e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153647"
---
# <a name="xml-documentation"></a>Dokumentacja XML

Można tworzyć dokumentację z trzema ukośnikami (/ / /) komentarzy w kodzie F#. Komentarze XML może znajdować się przed deklaracjami w kodu pliki (.fs) lub podpisu (.fsi).

## <a name="generating-documentation-from-comments"></a>Generowanie komentarzy dokumentacji

Obsługa w F# Generowanie komentarzy dokumentacji jest taka sama jak w innych językach .NET Framework. Tak jak w innych językach .NET Framework [-doc — opcja kompilatora](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) pozwala wygenerować plik XML, który zawiera informacje, które można przekształcić w dokumentacji, za pomocą narzędzia takiego jak Sandcastle. Dokumentacja wygenerowany przy użyciu narzędzia, które są przeznaczone do użytku z zestawów, które są zwykle zapisywane w innych językach .NET Framework wygenerować widok interfejsów API, który jest oparty na skompilowanej formy F# konstrukcji. Chyba, że narzędzia przeznaczone do obsługi F#, dokumentacja generowanych przez te narzędzia nie odpowiada F# widok interfejsu API.

Aby uzyskać więcej informacji na temat generowania dokumentacji z pliku XML, zobacz [komentarze dokumentacji XML &#40;C&#35; Programming Guide&#41;](https://msdn.microsoft.com/library/b2s063f7).

## <a name="recommended-tags"></a>Zalecane tagi

Istnieją dwa sposoby, aby zapisać komentarze dokumentacji XML. Jeden to wystarczy napisać dokumentację bezpośrednio w komentarzu potrójnym ukośnikiem, bez użycia tagów XML. Jeśli to zrobisz, cały tekst jest traktowana jako podsumowania dokumentacji konstrukcję kodu, który poprzedza. Użyj tej metody, gdy chcesz napisać tylko krótkie podsumowanie każdego konstrukcji. Inna metoda jest udostępnić więcej dokumentacji ze strukturą za pomocą tagów XML. Druga metoda, można określić oddzielne informacje o krótkie podsumowanie, dodatkowe uwagi, dokumentacji dla każdego parametru, parametr typu i wyjątki zgłaszane i opis wartości zwracanej. W poniższej tabeli opisano tagi XML, które są rozpoznawane w F# komentarzy kodu XML.

|Składnia znacznika|Opis|
|----------|-----------|
|**\<c\>**_tekstu_**\</c\>**|Określa, że *tekstu* jest kod. Ten tag może służyć przez generatory dokumentacji do wyświetlania tekstu w czcionkę, która jest odpowiednia dla kodu.|
|**\<Podsumowanie\>**_tekstu_ **\< /summary\>**|Określa, że *tekstu* znajduje się krótki opis elementu programu. Długość opisu jest zwykle jeden lub dwa zdania.|
|**\<Uwagi\>**_tekstu_ **\< /remarks\>**|Określa, że *tekstu* zawiera dodatkowe informacje o elemencie programu.|
|**\<param name = "**_nazwa_**"\>**_opis_**\</param\>**|Określa nazwę i opis parametru funkcji lub metody.|
|**\<typeparam name = "**_nazwa_**"\>**_opis_**\</typeparam\>**|Określa nazwę i opis dla parametru typu.|
|**\<Zwraca\>**_tekstu_ **\< /returns\>**|Określa, że *tekstu* opisuje wartość zwracaną funkcji lub metody.|
|**\<wyjątek cref = "**_typu_**"\>**_opis_**\</exception\>**|Określa typ wyjątku, który może zostać wygenerowany i okoliczności, w których jest generowany.|
|**\<patrz cref = "**_odwołania_**"\>**_tekstu_ **\< /see\>**|Określa wbudowany link prowadzący do innego elementu programu. *Odwołania* to nazwa, która jest wyświetlana w pliku dokumentacji XML. *Tekstu* jest tekst wyświetlany w linku.|
|**\<SeeAlso — cref = "**_odwołania_**" /\>**|Określa, zobacz też link do dokumentacji dla innego typu. *Odwołania* to nazwa, która jest wyświetlana w pliku dokumentacji XML. Zobacz też linki, które zwykle są wyświetlane w dolnej części strony dokumentacji.|
|**\<para\>**_tekstu_**\</para\>**|Określa akapit tekstu. To jest używany do oddzielania tekst wewnątrz **uwagi** tagu.|

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
