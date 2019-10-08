---
title: 'Porady: zapisywanie metody rozszerzenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: d01596d50db8ba1078e8ac82caa951418645c977
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004617"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Porady: zapisywanie metody rozszerzenia (Visual Basic)

Metody rozszerzające umożliwiają dodawanie metod do istniejącej klasy. Metodę rozszerzenia można wywołać tak, jakby była wystąpieniem tej klasy.

### <a name="to-define-an-extension-method"></a>Aby zdefiniować metodę rozszerzenia

1. Otwórz nową lub istniejącą aplikację Visual Basic w programie Visual Studio.

2. W górnej części pliku, w którym ma zostać zdefiniowana Metoda rozszerzenia, należy uwzględnić następujące instrukcje importu:

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. W module w nowej lub istniejącej aplikacji Rozpocznij Definiowanie metody z atrybutem [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) :

    ```vb
    <Extension()>
    ```
 
   Należy zauważyć, że atrybut `Extension` może być stosowany tylko do metody (`Sub` lub `Function` procedury) w [Module](../../../language-reference/statements/module-statement.md)Visual Basic. Jeśli zastosujesz go do metody w `Class` lub `Structure`, kompilator Visual Basic generuje błąd [BC36551](../../../misc/bc36551.md), "metody rozszerzające można definiować tylko w modułach".

4. Zadeklaruj metodę w zwykły sposób, z tą różnicą, że typ pierwszego parametru musi być typem danych, który ma zostać rozszerzona.

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a>Przykład

 Poniższy przykład deklaruje metodę rozszerzenia w module `StringExtensions`. Drugi moduł, `Module1`, importuje `StringExtensions` i wywołuje metodę. Metoda rozszerzająca musi znajdować się w zakresie, gdy jest wywoływana. Metoda rozszerzająca `PrintAndPunctuate` rozszerza klasę <xref:System.String> za pomocą metody, która wyświetla wystąpienie ciągu, po którym następuje ciąg symboli interpunkcyjnych wysłanych jako parametr.
  
```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

```vb
' Import the module that holds the extension method you want to use,
' and call it.

Imports ConsoleApplication2.StringExtensions

Module Module1
  
    Sub Main()
        Dim example = "Hello"
        example.PrintAndPunctuate("?")
        example.PrintAndPunctuate("!!!!")
    End Sub
    
End Module
```
  
 Należy zauważyć, że metoda jest zdefiniowana z dwoma parametrami i wywoływana z tylko jedną. Pierwszy parametr, `aString`, w definicji metody jest powiązany z `example`, wystąpieniem `String`, który wywołuje metodę. Dane wyjściowe przykładu są następujące:
  
 ```console
 Hello?
 Hello!!!!
 ```
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Metody rozszerzeń](extension-methods.md)
- [Module, instrukcja](../../../language-reference/statements/module-statement.md)
- [Parametry i argumenty procedur](procedure-parameters-and-arguments.md)
- [Zakres w Visual Basic](../declared-elements/scope.md)
