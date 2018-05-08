---
title: 'Porady: wywoływanie metody rozszerzenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 32691183bcd1632a82b1e9a2668790abbf8f80fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Porady: wywoływanie metody rozszerzenia (Visual Basic)
Metody rozszerzenia umożliwiają dodawanie metody do istniejącej klasy. Po — metoda rozszerzenia został zadeklarowany i dostosowane do zakresu, można wywołać go jak metodą wystąpienia typu, który rozszerza. Aby uzyskać więcej informacji na temat pisania metodę rozszerzenia, zobacz [porady: zapisywanie metody rozszerzenia](./how-to-write-an-extension-method.md).  
  
 Poniższe instrukcje dotyczą — metoda rozszerzenia `PrintAndPunctuate`, które zostaną wyświetlone wystąpienia ciągu, który wywołuje ona następuje niezależnie od wartości są wysyłane drugi parametr `punc`.  
  
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
  
 Metoda musi być w zakresie, gdy jest wywoływana.  
  
### <a name="to-call-an-extension-method"></a>Wywoływanie metody rozszerzenia  
  
1.  Deklarowanie zmiennej, która ma typ danych pierwszego parametru metody rozszerzającej. Aby uzyskać `PrintAndPunctuate`, należy <xref:System.String> zmienną:  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  Zmienna wywoła metodę rozszerzenia, czy wartość jest powiązany z pierwszym parametrem `aString`. Zostanie wyświetlona następująca instrukcja wywoływania `Ready?`.  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     Zwróć uwagę, że wywołanie tej metody rozszerzenia wygląda podobnie jak wywołania do jednego z <xref:System.String> wystąpienia metody, które wymagają jeden parametr:  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  Deklarowanie innej zmiennej ciągu i wywołać metodę ponownie, aby sprawdzić, czy działa z dowolnym ciągiem.  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     Wynik jest teraz: `or not!!!`.  
  
## <a name="example"></a>Przykład  
 Następujący kod jest kompletnym przykładem tworzenia i stosowania metody rozszerzenia proste.  
  
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
 [Instrukcje: zapisywanie metody rozszerzenia](./how-to-write-an-extension-method.md)  
 [Metody rozszerzeń](./extension-methods.md)  
 [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
