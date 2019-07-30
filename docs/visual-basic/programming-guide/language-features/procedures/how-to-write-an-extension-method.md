---
title: 'Instrukcje: Napisz metodę rozszerzenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 7a7a9d16d9f69071e9d1dacb0558f7ca92e1d21e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631031"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Instrukcje: Napisz metodę rozszerzenia (Visual Basic)
Metody rozszerzające umożliwiają dodawanie metod do istniejącej klasy. Metodę rozszerzenia można wywołać tak, jakby była wystąpieniem tej klasy.

### <a name="to-define-an-extension-method"></a>Aby zdefiniować metodę rozszerzenia

1. Otwórz nową lub istniejącą aplikację Visual Basic w programie Visual Studio.

2. W górnej części pliku, w którym ma zostać zdefiniowana Metoda rozszerzenia, należy uwzględnić następujące instrukcje importu:

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. W module w nowej lub istniejącej aplikacji Rozpocznij Definiowanie metody z atrybutem rozszerzenia:

    ```vb
    <Extension()>
    ```

4. Zadeklaruj metodę w zwykły sposób, z tą różnicą, że typ pierwszego parametru musi być typem danych, który ma zostać rozszerzona.

    ```vb
    <Extension()>
    Public Sub SubName (ByVal para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a>Przykład
 Poniższy przykład deklaruje metodę rozszerzenia w module `StringExtensions`. Drugi moduł `Module1`,, importuje `StringExtensions` i wywołuje metodę. Metoda rozszerzająca musi znajdować się w zakresie, gdy jest wywoływana. Metoda `PrintAndPunctuate` rozszerzająca <xref:System.String> rozszerza klasę z metodą, która wyświetla wystąpienie ciągu, po którym następuje ciąg symboli interpunkcyjnych wysłanych jako parametr.
  
```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
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
  
 Należy zauważyć, że metoda jest zdefiniowana z dwoma parametrami i wywoływana z tylko jedną. Pierwszy parametr `aString`, w definicji metody jest powiązany z `example`, wystąpieniem `String` wywołującym metodę. Dane wyjściowe przykładu są następujące:
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Metody rozszerzeń](./extension-methods.md)
- [Instrukcja Module](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
