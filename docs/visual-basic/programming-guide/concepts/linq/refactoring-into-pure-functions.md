---
title: Refaktoryzacja do czystych funkcji (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 0a37b30278c850256355612cec09a4c017c7adc2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379721"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a>Refaktoryzacja do czystych funkcji (Visual Basic)

Ważnym aspektem czystych przekształceń funkcjonalnych jest nauki refaktoryzacji kodu przy użyciu czystej funkcji.

Jak wspomniano wcześniej w tej sekcji, czystej funkcji ma dwie właściwości przydatne:

- Nie ma żadnych efektów ubocznych. Funkcja nie zmienia żadnych zmiennych lub danych dowolnego typu spoza tej funkcji.

- Jest ona zgodna. Biorąc pod uwagę ten sam zestaw danych wejściowych, która zawsze zwraca tę samą wartość w danych wyjściowych.

 Jednym ze sposobów przechodzenia do programowania funkcyjnego jest Przeprowadź refaktoryzację istniejącego kodu, aby wyeliminować niepotrzebne efekty uboczne i zależności zewnętrznych. W ten sposób można utworzyć wersji czystą funkcję istniejącego kodu.

W tym temacie omówiono funkcja czystego jest i co nie jest. [Samouczka: Manipulowanie zawartością w dokumencie WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) samouczek przedstawia sposób modyfikowania dokumentu WordprocessingML i zawiera dwa przykłady jak Refaktoryzacja, przy użyciu czystej funkcji.

## <a name="eliminating-side-effects-and-external-dependencies"></a>Eliminując skutki uboczne i zależności zewnętrznych

Poniższe przykłady porównać dwie funkcje — czyste i czystą funkcję.

### <a name="non-pure-function-that-changes-a-class-member"></a>Czystej funkcji, która zmienia składowej klasy

W poniższym kodzie `HyphenatedConcat` funkcja nie jest funkcją czystego, ponieważ modyfikuje `aMember` element członkowski danych w klasie:

```vb
Module Module1
    Dim aMember As String = "StringOne"

    Public Sub HyphenatedConcat(ByVal appendStr As String)
        aMember = aMember & "-" & appendStr
    End Sub

    Sub Main()
        HyphenatedConcat("StringTwo")
        Console.WriteLine(aMember)
    End Sub
End Module
```

Ten kod generuje następujące dane wyjściowe:

```
StringOne-StringTwo
```

Zwróć uwagę, że jej nie ma znaczenia tego, czy ma modyfikacji danych `public` lub `private` dostępu lub jest `shared` elementu członkowskiego lub elementu członkowskiego wystąpienia. Czystą funkcję nie zmienia żadnych danych poza funkcją.

### <a name="non-pure-function-that-changes-an-argument"></a>Czystej funkcji, która zmienia argumentu

Ponadto, następująca wersja tej samej funkcji nie jest czysty ponieważ modyfikuje zawartość jako parametr `sb`.

```vb
Module Module1
    Public Sub HyphenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)
        sb.Append("-" & appendStr)
    End Sub

    Sub Main()
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")
        HyphenatedConcat(sb1, "StringTwo")
        Console.WriteLine(sb1)
    End Sub
End Module
```

Ta wersja programu daje takie same dane wyjściowe jako pierwsza wersja, ponieważ `HyphenatedConcat` funkcja została zmieniona wartość (stan) jako pierwszy parametr, wywołując <xref:System.Text.StringBuilder.Append%2A> funkcja elementu członkowskiego. Uwaga występowanie tej zmiany, pomimo faktu, `HyphenatedConcat` używa wywołań przez wartość parametru przekazywania.

> [!IMPORTANT]
> Dla typów odwołań w przypadku przekazania parametr przez wartość, jej powoduje kopię odwołanie do obiektu przekazywana. Ta kopia jest nadal skojarzone z tymi samymi danymi wystąpienia jako odwołanie do oryginalnego (aż do zmiennej odwołania jest przypisany do nowego obiektu). Wywołanie przez odwołanie nie jest zawsze wymagane dla funkcji zmodyfikować parametr.

### <a name="pure-function"></a>Czystej funkcji

Ten następnej wersji programu, jak wybierać sposób implementacji `HyphenatedConcat` pełnią czystą funkcję.

```vb
Module Module1
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String
        Return (s & "-" & appendStr)
    End Function

    Sub Main()
        Dim s1 As String = "StringOne"
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")
        Console.WriteLine(s2)
    End Sub
End Module
```

Ponownie generuje ten sam wiersz danych wyjściowych w tej wersji: `StringOne-StringTwo`. Należy pamiętać, aby zachować wartość połączone, jest on przechowywany w zmiennej pośrednich `s2`.

Jedno podejście, które mogą być bardzo przydatne jest napisanie funkcje, które są lokalnie oczyścić zanieczyszczony (oznacza to, mogą zadeklarować i modyfikowanie zmiennych lokalnych), ale są globalnie czysty. Takie funkcje, ma wiele cech pożądane możliwości tworzenia, ale uniknąć niektórych bardziej zawiłe funkcjonalności idiomy programowania, takich jak konieczności rekursję, gdy prostej pętli może osiągnąć to samo.

## <a name="standard-query-operators"></a>Standardowe operatory zapytań

Ważną cechą standardowych operatorów zapytań jest, że są implementowane jako czystych funkcji.

Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — Przegląd (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do czystych przekształceń funkcjonalnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Programowanie funkcjonalne a Programowanie imperatywne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
