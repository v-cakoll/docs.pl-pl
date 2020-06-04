---
title: 'Porady: wywoływanie metody rozszerzenia'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 54419c99ae08c9ca2e3cfa86993dc99bc02bbb64
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388663"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Porady: wywoływanie metody rozszerzenia (Visual Basic)

Metody rozszerzające umożliwiają dodawanie metod do istniejącej klasy. Po zadeklarowaniu i wejściu do zakresu metody rozszerzenia można wywołać ją jak metodę wystąpienia typu, który rozszerza. Aby uzyskać więcej informacji na temat pisania metody rozszerzenia, zobacz [How to: Write a Extension Method](./how-to-write-an-extension-method.md).

 Poniższe instrukcje odnoszą się do metody rozszerzającej `PrintAndPunctuate` , która wyświetla wystąpienie ciągu, które wywołuje ten element, a następnie dowolną wartość jest wysyłana w dla drugiego parametru, `punc` .

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

1. Zadeklaruj zmienną, która ma typ danych pierwszego parametru metody rozszerzenia. Dla `PrintAndPunctuate` , potrzebna jest <xref:System.String> zmienna:

    ```vb
    Dim example = "Ready"
    ```

2. Ta zmienna wywoła metodę rozszerzającą, a jej wartość jest powiązana z pierwszym parametrem `aString` . Zostanie wyświetlona następująca instrukcja wywołująca `Ready?` .

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

     Wynik tego czasu: `or not!!!` .

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

## <a name="see-also"></a>Zobacz też

- [Porady: zapisywanie metody rozszerzenia](./how-to-write-an-extension-method.md)
- [Metody rozszerzające](./extension-methods.md)
- [Zakres w Visual Basic](../declared-elements/scope.md)
