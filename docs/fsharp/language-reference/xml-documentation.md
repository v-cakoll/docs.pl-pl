---
title: Dokumentacja XML (F#)
description: Dowiedz się więcej F# o pomocy technicznej w programie w celu wygenerowania dokumentacji z komentarzy.
ms.date: 05/16/2016
ms.openlocfilehash: b89ab4117f4dd71126f8e203f4a5271ab3c30021
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630821"
---
# <a name="xml-documentation"></a>Dokumentacja XML

W programie można utworzyć dokumentację z komentarzy do F#kodu potrójnym ukośnikiem (//). Komentarze XML mogą poprzedzać deklaracje w plikach kodu (. FS) lub sygnatur (. FSI).

## <a name="generating-documentation-from-comments"></a>Generowanie dokumentacji z komentarzy

Pomoc techniczna w F# przypadku generowania dokumentacji z komentarzy jest taka sama jak w innych językach .NET Framework. Podobnie jak w innych językach .NET Framework, [Opcja kompilatora-doc](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) umożliwia tworzenie pliku XML, który zawiera informacje, które można skonwertować do dokumentacji przy użyciu narzędzia, takiego jak [DocFX](https://dotnet.github.io/docfx/) lub [Sandcastle](https://github.com/EWSoftware/SHFB). Dokumentacja wygenerowana przy użyciu narzędzi przeznaczonych do użytku z zestawami, które są napisane w innych językach .NET Framework zwykle przedstawia widok interfejsów API opartych na skompilowanej formie F# konstrukcji. Jeśli narzędzia specjalne nie F#obsługują, dokumentacja wytworzona przez te narzędzia nie jest F# zgodna z widokiem interfejsu API.

Aby uzyskać więcej informacji o sposobach generowania dokumentacji z pliku XML, zobacz [Dokumentacja &#40;dokumentacji&#35; XML C&#41;Przewodnik programowania](https://msdn.microsoft.com/library/b2s063f7).

## <a name="recommended-tags"></a>Zalecane Tagi

Istnieją dwa sposoby zapisywania komentarzy do dokumentacji XML. Po prostu napisz dokumentację bezpośrednio w komentarzu z potrójnym ukośnikiem, bez używania tagów XML. Jeśli to zrobisz, cały tekst komentarza jest traktowany jako dokumentacja podsumowania konstrukcji kodu, która jest bezpośrednio następująca. Użyj tej metody, jeśli chcesz napisać tylko krótkie podsumowanie dla każdej konstrukcji. Druga metoda polega na użyciu tagów XML w celu zapewnienia większej dokumentacji strukturalnej. Druga metoda pozwala określić oddzielne notatki dla krótkiego podsumowania, dodatkowe uwagi, dokumentację dla każdego parametru i parametru typu oraz zgłoszone wyjątki oraz opis wartości zwracanej. W poniższej tabeli opisano tagi XML, które są rozpoznawane w F# komentarzach kodu XML.

|Składnia tagów|Opis|
|----------|-----------|
|_tekst_ **c/c\> \<** **\<\>**|Określa, że *tekst* jest kodem. Ten tag może być używany przez generatory dokumentacji do wyświetlania tekstu w czcionce, która jest odpowiednia dla kodu.|
|**Podsumowanietekstu\>/Summary \<** **\<\>**|Określa, że *tekst* jest krótkim opisem elementu programu. Opis jest zwykle jednym lub dwoma zdaniami.|
|**uwagitekstowe\>/Remarks \<** **\<\>**|Określa, że *tekst* zawiera dodatkowe informacje o elemencie program.|
|**\>**  **param\<Name = "** Name"**Description/param\<\>**|Określa nazwę i opis parametru funkcji lub metody.|
|**\>**  **typeparam\<Name = "** Name"**Description/typeparam\<\>**|Określa nazwę i opis parametru typu.|
|**zwracatekst\>/Returns \<** **\<\>**|Określa, że *tekst* opisuje wartość zwracaną przez funkcję lub metodę.|
|**\>**  **Exception\<cref = "** Type"**Description/Exception\<\>**|Określa typ wyjątku, który może być wygenerowany i okoliczności, w których jest generowany.|
|**\>**  **Zobacz\<cref = "** Reference"**Text/See\<\>**|Określa link wbudowany do innego elementu programu. *Odwołanie* jest nazwą wyświetlaną w pliku dokumentacji XML. *Tekst* jest tekstem wyświetlanym w łączu.|
|**\>** seealso — cref = "odwołanie"/  **\<**|Określa również link do dokumentacji dla innego typu. *Odwołanie* jest nazwą wyświetlaną w pliku dokumentacji XML. Zobacz także linki zwykle wyświetlane w dolnej części strony dokumentacji.|
|**\>/para \<** _tekstu_**akapitu\<\>**|Określa akapit tekstu. Służy do rozdzielania tekstu wewnątrz znacznika **uwagi** .|

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniżej znajduje się typowy komentarz dokumentacji XML w pliku sygnatury.

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład pokazuje alternatywną metodę bez tagów XML. W tym przykładzie cały tekst w komentarzu jest traktowany jako podsumowanie. Należy pamiętać, że jeśli nie określisz jawnie tagu podsumowującego, nie należy określać innych tagów, takich jak **param** lub **zwracających** Tagi.

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Opcje kompilatora](compiler-options.md)
