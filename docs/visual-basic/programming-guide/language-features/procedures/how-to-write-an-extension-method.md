---
title: 'Instrukcje: Zapisywanie metody rozszerzenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: d6f8b85945bd400d1f4b54a50260d72c750add8b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819120"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Instrukcje: Zapisywanie metody rozszerzenia (Visual Basic)
Metody rozszerzające umożliwiają dodawanie metod do istniejącej klasy. Metoda rozszerzenia może być wywoływana, jakby była wystąpieniem tej klasy.  
  
### <a name="to-define-an-extension-method"></a>Aby zdefiniować metodę rozszerzenia  
  
1.  Otwieranie nowej lub istniejącej aplikacji języka Visual Basic w programie Visual Studio.  
  
2.  W górnej części pliku, w której chcesz zdefiniować metodę rozszerzenia obejmują następującą instrukcję import:  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  W module w nowej lub istniejącej aplikacji Rozpocznij definicję metody z atrybutem rozszerzenia:  
  
    ```  
    <Extension()>  
    ```  
  
4.  Zadeklaruj metodę w zwykły sposób, z tą różnicą, że typ pierwszego parametru musi być typu danych, które chcesz rozszerzyć.  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje metodę rozszerzenia w module `StringExtensions`. Drugi moduł `Module1`, importuje `StringExtensions` i wywołuje metodę. Metoda rozszerzenia musi być w zakresie, gdy jest wywoływana. Metoda rozszerzenia `PrintAndPunctuate` rozszerza <xref:System.String> klasę z metodą, która wyświetla wystąpienia ciągu następuje ciąg symbole znaków interpunkcyjnych wysyłane jako parametr.  
  
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
  
 Należy zauważyć, że metoda jest zdefiniowana za pomocą dwóch parametrów i wywoływana tylko z jednym. Pierwszy parametr `aString`, w metodzie definicji jest powiązany z `example`, wystąpienie `String` , wywołuje metodę. Dane wyjściowe z przykładu jest następująca:  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Metody rozszerzeń](./extension-methods.md)
- [Instrukcja Module](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
