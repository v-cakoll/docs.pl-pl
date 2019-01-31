---
title: Nie można używać metod typu „System.Nullable(Of T)” jako operandów operatora „AddressOf”.
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 59e89b24eca6a034dc1df2216f6f0d68e8191a18
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278567"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a>Nie można używać metod typu „System.Nullable(Of T)” jako operandów operatora „AddressOf”.
Instrukcja używa `AddressOf` operatora z argumentem, który reprezentuje procedurę <xref:System.Nullable%601> struktury.  
  
 **Identyfikator błędu:** BC32126  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zamień nazwę procedury w `AddressOf` klauzuli z argumentem, który nie jest członkiem <xref:System.Nullable%601>.  
  
-   Napisać klasę, która otacza metody <xref:System.Nullable%601> , którego chcesz użyć. W poniższym przykładzie `NullableWrapper` klasa definiuje nową metodę o nazwie `GetValueOrDefault`. Ponieważ ta nowa metoda nie jest członkiem <xref:System.Nullable%601>, mogą być stosowane do `nullInstance`, wystąpienie typu dopuszczającego wartość null w celu utworzenia argument `AddressOf`.  
  
```vb  
Module Module1  
  
    Delegate Function Deleg() As Integer  
  
    Sub Main()  
        Dim nullInstance As New Nullable(Of Integer)(1)  
  
        Dim del As Deleg  
  
        ' GetValueOrDefault is a method of the Nullable generic  
        ' type. It cannot be used as an operand of AddressOf.  
        ' del = AddressOf nullInstance.GetValueOrDefault  
  
        ' The following line uses the GetValueOrDefault method  
        ' defined in the NullableWrapper class.  
        del = AddressOf (New NullableWrapper(  
            Of Integer)(nullInstance)).GetValueOrDefault  
  
        Console.WriteLine(del.Invoke())  
    End Sub  
  
    Class NullableWrapper(Of T As Structure)  
        Private m_Value As Nullable(Of T)  
  
        Sub New(ByVal Value As Nullable(Of T))  
            m_Value = Value  
        End Sub  
  
        Public Function GetValueOrDefault() As T  
            Return m_Value.Value  
        End Function  
    End Class  
End Module  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Nullable%601>
- [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Typy wartości dopuszczających wartości null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
