---
title: Funkcje ciągów
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 778e57eadd75baf1aabd100f9d8d41a490f79a04
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406291"
---
# <a name="string-functions-visual-basic"></a>Funkcje ciągów (Visual Basic)

Poniższa tabela zawiera listę funkcji, które Visual Basic zapewnia w <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> klasie w celu wyszukiwania ciągów i manipulowania nimi. Mogą być uznawane za Visual Basic funkcje wewnętrzne; oznacza to, że nie trzeba wywoływać ich jako jawnych elementów członkowskich klasy, jak pokazano w przykładzie. Dodatkowe metody, a w niektórych przypadkach metody uzupełniające są dostępne w <xref:System.String?displayProperty=nameWithType> klasie.

|.NET Framework, Metoda|Opis|
|---------------------------|-----------------|
|<xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>|Zwraca `Integer` wartość reprezentującą kod znaku odpowiadający znakowi.|
|<xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>|Zwraca znak skojarzony z podanym kodem znaku.|
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|Zwraca tablicę opartą na zero, zawierającą podzbiór `String` tablicy na podstawie określonych kryteriów filtrowania.|
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|Zwraca ciąg sformatowany zgodnie z instrukcjami zawartymi w `String` wyrażeniu formatu.|
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|Zwraca wyrażenie sformatowane jako wartość walutowa przy użyciu symbolu waluty zdefiniowanego w panelu sterowania systemem.|
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|Zwraca wyrażenie ciągu reprezentujące wartość daty/godziny.|
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|Zwraca wyrażenie sformatowane jako liczba.|
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|Zwraca wyrażenie sformatowane jako wartość procentowa (czyli pomnożona przez 100) z końcowym znakiem%.|
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|Zwraca liczbę całkowitą określającą pozycję początkową pierwszego wystąpienia jednego ciągu w innym.|
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|Zwraca pozycję pierwszego wystąpienia jednego ciągu w innym, rozpoczynając od prawej strony ciągu.|
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|Zwraca ciąg utworzony przez przyłączenie kilku podciągów zawartych w tablicy.|
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|Zwraca ciąg lub znak przekonwertowany na małe litery.|
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|Zwraca ciąg zawierający określoną liczbę znaków z lewej strony ciągu.|
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|Zwraca liczbę całkowitą, która zawiera numer znaków w ciągu.|
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|Zwraca ciąg wyrównany do lewej zawierający określony ciąg dostosowany do określonej długości.|
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|Zwraca ciąg zawierający kopię określonego ciągu bez spacji wiodących.|
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|Zwraca ciąg zawierający określoną liczbę znaków z ciągu.|
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|Zwraca ciąg, w którym określony podciąg został zamieniony na inny podciąg określoną liczbę razy.|
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|Zwraca ciąg zawierający określoną liczbę znaków z prawej strony ciągu.|
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|Zwraca ciąg wyrównany do prawej zawierający określony ciąg dostosowany do określonej długości.|
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|Zwraca ciąg zawierający kopię określonego ciągu bez spacji końcowych.|
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|Zwraca ciąg zawierający podaną liczbę spacji.|
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|Zwraca tablicę jednowymiarową (od zera) zawierającą określoną liczbę podciągów.|
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|Zwraca wartość-1, 0 lub 1, na podstawie wyniku porównania ciągów.|
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|Zwraca ciąg przekonwertowany jako określony.|
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|Zwraca ciąg lub obiekt składający się z określonego znaku Powtórzonego określoną liczbę razy.|
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|Zwraca ciąg, w którym kolejność znaków określonego ciągu jest odwrócona.|
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|Zwraca ciąg zawierający kopię określonego ciągu bez spacji wiodących i końcowych.|
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|Zwraca ciąg lub znak zawierający określony ciąg przekonwertowany na wielkie litery.|

Możesz użyć instrukcji [Compare](../statements/option-compare-statement.md) , aby określić, czy ciągi są porównywane przy użyciu kolejności sortowania tekstu nieuwzględniającego wielkości liter, określonego przez ustawienia regionalne systemu ( `Text` ) lub wewnętrzne reprezentacje binarne znaków ( `Binary` ). Domyślną metodą porównywania tekstu jest `Binary` .

## <a name="example-ucase"></a>Przykład: UCase

Ten przykład używa `UCase` funkcji, aby zwrócić wielką wersję ciągu.
[!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]

## <a name="example-ltrim"></a>Przykład: LTrim

Ten przykład używa funkcji, aby rozdzielić `LTrim` wiodące spacje i funkcję, aby rozdzielić `RTrim` spacje ze zmiennej ciągu. Używa funkcji, `Trim` Aby rozdzielić oba typy spacji.

[!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]

## <a name="example-mid"></a>Przykład: Mid

W tym przykładzie `Mid` Funkcja zwraca określoną liczbę znaków z ciągu.

[!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]

## <a name="example-len"></a>Przykład: Len

Ten przykład używa `Len` do zwracania liczby znaków w ciągu.

[!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]

## <a name="example-instr"></a>Przykład: InStr

Ten przykład używa `InStr` funkcji, aby zwrócić pozycję pierwszego wystąpienia jednego ciągu w innym.

[!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]

## <a name="example-format"></a>Przykład: format

W tym przykładzie pokazano różne zastosowania `Format` funkcji do formatowania wartości przy użyciu formatów `String` i formatów zdefiniowanych przez użytkownika. W przypadku separatora daty ( `/` ), separatora czasu ( `:` ) i wskaźników am/pm ( `t` i `tt` ) rzeczywiste sformatowane dane wyjściowe wyświetlane przez system są zależne od ustawień regionalnych, których używa kod. Gdy godziny i daty są wyświetlane w środowisku deweloperskim, używany jest format krótki czas i krótki format daty dla ustawień regionalnych.

> [!NOTE]
> Dla ustawień regionalnych, które używają zegara 24-godzinnego, wskaźniki AM/PM ( `t` i `tt` ) nie wyświetlają niczego.

[!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]

## <a name="see-also"></a>Zobacz też

- [Słowa kluczowe](../keywords/index.md)
- [Elementy członkowskie biblioteki wykonawczej programu Visual Basic](../runtime-library-members.md)
- [Manipulowanie ciągami — podsumowanie](../keywords/string-manipulation-summary.md)
- [Metody klasy System. String](xref:System.String#methods)
