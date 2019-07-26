---
title: 'Instrukcje: Wywoływanie metody rozszerzenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: f2058162ab939d2619d7255c884d88c35ee63715
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512673"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Instrukcje: Wywoływanie metody rozszerzenia (Visual Basic)

Metody rozszerzające umożliwiają dodawanie metod do istniejącej klasy. Po zadeklarowaniu i wejściu do zakresu metody rozszerzenia można wywołać ją jak metodę wystąpienia typu, który rozszerza. Aby uzyskać więcej informacji na temat pisania metody rozszerzenia, zobacz [How to: Napisz metodę](./how-to-write-an-extension-method.md)rozszerzenia.

 Poniższe instrukcje odnoszą się do metody `PrintAndPunctuate`rozszerzającej, która wyświetla wystąpienie ciągu, które wywołuje ten element, a następnie dowolną wartość jest wysyłana w dla drugiego `punc`parametru,.

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

Metoda musi znajdować się w zakresie, gdy jest wywoływana.

### <a name="to-call-an-extension-method"></a>Aby wywołać metodę rozszerzenia

1. Zadeklaruj zmienną, która ma typ danych pierwszego parametru metody rozszerzenia. Dla `PrintAndPunctuate`, potrzebna jest <xref:System.String> zmienna:

    ```vb
    Dim example = "Ready"
    ```

2. Ta zmienna wywoła metodę rozszerzającą, a jej wartość jest powiązana z pierwszym parametrem `aString`. Zostanie wyświetlona `Ready?`następująca instrukcja wywołująca.

    ```vb
    example.PrintAndPunctuate("?")
    ```

     Zwróć uwagę, że wywołanie tej metody rozszerzenia wygląda tak samo jak wywołanie jednej z <xref:System.String> metod instancji, które wymagają jednego parametru:

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. Zadeklaruj inną zmienną ciągu i Wywołaj metodę ponownie, aby zobaczyć, że działa z dowolnym ciągiem.

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     Wynik tego czasu: `or not!!!`.

## <a name="example"></a>Przykład
 Poniższy kod stanowi kompletny przykład tworzenia i używania prostej metody rozszerzenia.

```vb
Imports System.Runtime.CompilerServices
Imports ConsoleApplication1.StringExtensions

Module Module1

    Sub Main()

        Dim example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")

        Dim example2 = "Goodbye"
        example2.PrintAndPunctuate("?")
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module

' Output:
' Hello.
' Hello!!!!
' Goodbye?
```

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Napisz metodę rozszerzenia](./how-to-write-an-extension-method.md)
- [Metody rozszerzeń](./extension-methods.md)
- [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
