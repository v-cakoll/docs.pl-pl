---
title: 'Porady: wywoływanie metody rozszerzenia'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: a19705a8f90833d48869df26a18d19b0ad1488e0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340397"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Porady: wywoływanie metody rozszerzenia (Visual Basic)

Metody rozszerzające umożliwiają dodawanie metod do istniejącej klasy. Po zadeklarowaniu i wejściu do zakresu metody rozszerzenia można wywołać ją jak metodę wystąpienia typu, który rozszerza. Aby uzyskać więcej informacji na temat pisania metody rozszerzenia, zobacz [How to: Write a Extension Method](./how-to-write-an-extension-method.md).

 Poniższe instrukcje odnoszą się do metody rozszerzenia `PrintAndPunctuate`, która będzie wyświetlać wystąpienie ciągu, które wywołuje ten element, a następnie dowolną wartość jest wysyłana w dla drugiego parametru, `punc`.

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

1. Zadeklaruj zmienną, która ma typ danych pierwszego parametru metody rozszerzenia. W przypadku `PrintAndPunctuate`potrzebna jest zmienna <xref:System.String>:

    ```vb
    Dim example = "Ready"
    ```

2. Ta zmienna wywoła metodę rozszerzającą, a jej wartość jest powiązana z pierwszym parametrem, `aString`. Następująca instrukcja wywołująca wyświetli `Ready?`.

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

     Wynik tego czasu to: `or not!!!`.

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

- [Instrukcje: zapisywanie metody rozszerzenia](./how-to-write-an-extension-method.md)
- [Metody rozszerzeń](./extension-methods.md)
- [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
