---
title: Nie można używać metod typu „System.Nullable(Of T)” jako operandów operatora „AddressOf”.
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 61c6fe7c33b3292066e653304ded43a863413723
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397223"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a>Nie można używać metod typu „System.Nullable(Of T)” jako operandów operatora „AddressOf”.
Instrukcja używa `AddressOf` operatora z operandem, który reprezentuje procedurę <xref:System.Nullable%601> struktury.  
  
 **Identyfikator błędu:** BC32126  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zastąp nazwę procedury w `AddressOf` klauzuli argumentem, który nie jest elementem członkowskim <xref:System.Nullable%601> .  
  
- Napisz klasę, która otacza metodę <xref:System.Nullable%601> , której chcesz użyć. W poniższym przykładzie `NullableWrapper` Klasa definiuje nową metodę o nazwie `GetValueOrDefault` . Ponieważ ta nowa metoda nie jest elementem członkowskim <xref:System.Nullable%601> , można jej zastosować do `nullInstance` , wystąpienia typu dopuszczającego wartość null, aby utworzyć argument dla `AddressOf` .  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Nullable%601>
- [AddressOf, operator](../operators/addressof-operator.md)
- [Typy wartości null](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Typy ogólne w Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
