---
title: Refaktoryzacja do czystych funkcji
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 22b371c6136836d6e0f1281f824b69378c0d3e4a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346521"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a>Refaktoryzacja do czystych funkcji (Visual Basic)

Ważnym aspektem czystych transformacji funkcjonalnych jest uczenie się, jak kod refaktoryzacji przy użyciu czystych funkcji.

Jak wspomniano wcześniej w tej sekcji, czysta funkcja ma dwie przydatne cechy:

- Nie ma żadnych efektów ubocznych. Funkcja nie zmienia żadnych zmiennych ani danych dowolnego typu poza funkcją.

- Jest ona spójna. Mając ten sam zestaw danych wejściowych, zawsze zwróci tę samą wartość wyjściową.

 Jednym ze sposobów przejścia do programowania funkcjonalnego jest Refaktoryzacja istniejącego kodu w celu wyeliminowania zbędnych efektów ubocznych i zewnętrznych zależności. W ten sposób można utworzyć czystą wersję funkcji istniejącego kodu.

W tym temacie omówiono czystą funkcję i jej znaczenie. [Samouczek: manipulowanie zawartością w samouczku WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) pokazuje, jak manipulować dokumentem WordprocessingML i zawiera dwa przykłady sposobu refaktoryzacji przy użyciu czystej funkcji.

## <a name="eliminating-side-effects-and-external-dependencies"></a>Eliminowanie efektów ubocznych i zależności zewnętrznych

Poniższe przykłady różnią się dwoma nieczystymi funkcjami i czystą funkcją.

### <a name="non-pure-function-that-changes-a-class-member"></a>Nieczysta funkcja, która zmienia element członkowski klasy

W poniższym kodzie funkcja `HyphenatedConcat` nie jest czystą funkcją, ponieważ modyfikuje element członkowski danych `aMember` w klasie:

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

```console
StringOne-StringTwo
```

Należy zauważyć, że nie ma znaczenia, czy modyfikowane dane mają `public` czy `private` dostępu, czy też jest członkiem `shared` lub członkiem wystąpienia. Czysta funkcja nie zmienia żadnych danych poza funkcją.

### <a name="non-pure-function-that-changes-an-argument"></a>Nieczysta funkcja, która zmienia argument

Ponadto następująca wersja tej samej funkcji nie jest czysta, ponieważ modyfikuje zawartość jej parametru, `sb`.

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

Ta wersja programu daje te same dane wyjściowe co w pierwszej wersji, ponieważ funkcja `HyphenatedConcat` zmieniła wartość (stan) pierwszego parametru przez wywołanie funkcji członkowskiej <xref:System.Text.StringBuilder.Append%2A>. Należy zauważyć, że ta zmiana występuje pomimo tego, że `HyphenatedConcat` używa parametrów wywołania-do-wartości.

> [!IMPORTANT]
> W przypadku typów referencyjnych, Jeśli przekażesz parametr według wartości, wynikiem jest kopia odwołania do obiektu, który jest przekazywany. Ta kopia jest nadal skojarzona z tymi samymi danymi wystąpienia co oryginalne odwołanie (do momentu przypisania zmiennej odniesienia do nowego obiektu). Wywołanie przez odwołanie nie musi być wymagane do zmodyfikowania parametru przez funkcję.

### <a name="pure-function"></a>Czysta funkcja

Ta Następna wersja programu hows sposób implementacji funkcji `HyphenatedConcat` jako czystej funkcji.

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

Ta wersja generuje ten sam wiersz danych wyjściowych: `StringOne-StringTwo`. Należy pamiętać, że aby zachować łączną wartość, jest ona przechowywana w zmiennej pośredniej `s2`.

Jednym z metod, które może być bardzo przydatne, jest zapisanie funkcji, które są w sposób nieczysty (to oznacza, że deklarują i modyfikują zmienne lokalne), ale są globalnie czyste. Takie funkcje mają wiele pożądanych cech tworzenia, ale unikają niektórych bardziej zawiłeych idiomy programowania, takich jak korzystanie z rekursji, gdy pętla prosta osiągnie tę samą wartość.

## <a name="standard-query-operators"></a>Standardowe operatory zapytań

Ważną cechą standardowych operatorów zapytań jest zaimplementowanie ich jako czystych funkcji.

Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — Omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do czystych transformacji funkcjonalnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Programowanie funkcjonalne a programowanie bezwzględne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
