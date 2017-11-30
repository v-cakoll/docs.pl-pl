---
title: 'Porady: zapisywanie metody rozszerzenia (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65cdabf59886e7457a327ee9cde968a6a73f2280
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Porady: zapisywanie metody rozszerzenia (Visual Basic)
Metody rozszerzenia umożliwiają dodawanie metody do istniejącej klasy. Tak, jakby była wystąpienia tej klasy można wywołać metody rozszerzenia.  
  
### <a name="to-define-an-extension-method"></a>Aby zdefiniować — metoda rozszerzenia  
  
1.  Otwieranie nowej lub istniejącej aplikacji Visual Basic w programie Visual Studio.  
  
2.  W górnej części pliku, w którym chcesz zdefiniować metodę rozszerzenia należy uwzględnić następującą instrukcję import:  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  W module w nowej lub istniejącej aplikacji Rozpocznij definicja metody z atrybutem rozszerzenia:  
  
    ```  
    <Extension()>  
    ```  
  
4.  Zadeklaruj metodę w zwykły sposób, z tą różnicą, że typ pierwszego parametru musi być typu danych, który ma zostać rozszerzony.  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje metody rozszerzenia w module `StringExtensions`. Drugi moduł `Module1`, importuje `StringExtensions` i wywołuje metodę. Metoda rozszerzenia musi być w zakresie, gdy jest wywoływana. Metody rozszerzenia `PrintAndPunctuate` rozszerza <xref:System.String> klasy za pomocą metody, która wyświetla wystąpienia ciągu następuje ciąg znaków specjalnych wysyłane w jako parametr.  
  
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
  
 Zwróć uwagę, że metoda jest zdefiniowana z dwoma parametrami i wywołać tylko z jednym. Pierwszy parametr `aString`, w metodzie definicji jest powiązany z `example`, wystąpienie `String` która wywołuje metodę. Dane wyjściowe przykładzie ma następującą składnię:  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [Metody rozszerzenia](./extension-methods.md)  
 [Module — instrukcja](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
