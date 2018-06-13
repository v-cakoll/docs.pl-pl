---
title: Metody &#39;System.Nullable (Of T)&#39; nie można używać jako argumentów &#39;AddressOf&#39; — operator
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 3a3e4fc033f47fb6a72076dff79f1eece8d01a30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594123"
---
# <a name="methods-of-39systemnullableof-t39-cannot-be-used-as-operands-of-the-39addressof39-operator"></a>Metody &#39;System.Nullable (Of T)&#39; nie można używać jako argumentów &#39;AddressOf&#39; — operator
Używa instrukcji `AddressOf` operatora z argumentem, który reprezentuje procedurę <xref:System.Nullable%601> struktury.  
  
 **Identyfikator błędu:** BC32126  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zamień nazwę procedury w `AddressOf` klauzuli z argumentem, który nie jest elementem członkowskim <xref:System.Nullable%601>.  
  
-   Klasa, która opakowuje metody zapisu <xref:System.Nullable%601> którego chcesz używać. W poniższym przykładzie `NullableWrapper` klasa definiuje nową metodę o nazwie `GetValueOrDefault`. Ponieważ ta nowa metoda nie jest elementem członkowskim <xref:System.Nullable%601>, mogą być stosowane do `nullInstance`, wystąpienia typu wartości null do utworzenia argument `AddressOf`.  
  
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
 <xref:System.Nullable%601>  
 [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Typy wartości dopuszczających wartości null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
