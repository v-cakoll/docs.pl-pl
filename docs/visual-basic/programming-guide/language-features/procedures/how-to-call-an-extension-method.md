---
title: 'Instrukcje: Wywoływanie metody rozszerzenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 4e9391a4c4a159cd5e198689bf7af7cd64c3a872
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620451"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Instrukcje: Wywoływanie metody rozszerzenia (Visual Basic)
Metody rozszerzające umożliwiają dodawanie metod do istniejącej klasy. Po metody rozszerzenia są deklarowane i dostosowane do zakresu, można też wywołać, takich jak metoda wystąpienia typu, który stanowi rozszerzenie. Aby uzyskać więcej informacji na temat pisania metodę rozszerzenia, zobacz [jak: Zapisywanie metody rozszerzenia](./how-to-write-an-extension-method.md).  
  
 Poniższe instrukcje dotyczą — metoda rozszerzenia `PrintAndPunctuate`, co spowoduje wyświetlenie wystąpieniu ciągu, który wywołuje on następuje niezależnie od wartości wysyłane jako drugi parametr `punc`.  
  
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
  
### <a name="to-call-an-extension-method"></a>Aby wywołać metodę rozszerzenia  
  
1.  Zadeklaruj zmienną, która ma typ danych pierwszy parametr metody rozszerzenia. Aby uzyskać `PrintAndPunctuate`, potrzebujesz <xref:System.String> zmiennej:  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  Czy zmienna spowoduje wywołanie metody rozszerzenia, a jego wartość jest związana z pierwszego parametru `aString`. Zostanie wyświetlona następująca instrukcja wywoływania `Ready?`.  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     Należy zauważyć, że wywołanie tej metody rozszerzenia wygląda po prostu, takie jak wywołanie jednej z <xref:System.String> wystąpienia metody, które wymagają jednego parametru:  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  Zadeklaruj innej zmiennej ciągu i wywołanie metody ponownie, aby zobaczyć, czy działa z dowolnym ciągiem.  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     Wynik jest w tej chwili: `or not!!!`.  
  
## <a name="example"></a>Przykład  
 Poniższy kod jest kompletny przykład tworzenia i używania metody proste rozszerzenie.  
  
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
- [Instrukcje: Zapisywanie metody rozszerzenia](./how-to-write-an-extension-method.md)
- [Metody rozszerzeń](./extension-methods.md)
- [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
