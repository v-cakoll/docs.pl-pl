---
title: Of, klauzula
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: 8497f46453d586fb94e1f7c82c81c6b923dd6f60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404424"
---
# <a name="of-clause-visual-basic"></a>Of — Klauzula (Visual Basic)
Wprowadza `Of` klauzulę, która identyfikuje *parametr typu* dla klasy *ogólnej* , struktury, interfejsu, delegata lub procedury. Aby uzyskać informacje na temat typów ogólnych, zobacz [typy ogólne w Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Za pomocą słowa kluczowego  
 Poniższy przykład kodu używa `Of` słowa kluczowego do definiowania konspektu klasy, która przyjmuje dwa parametry typu. *Ogranicza* `keyType` parametr według <xref:System.IComparable> interfejsu, co oznacza, że kod zużywający musi dostarczyć argument typu, który implementuje <xref:System.IComparable> . Jest to konieczne, aby `add` procedura mogła wywołać <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> metodę. Aby uzyskać więcej informacji o ograniczeniach, zobacz [Type list](type-list.md).  
  
```vb  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 Jeśli poprzednia definicja klasy zostanie ukończona, można utworzyć `dictionary` z niej różne klasy. Typy, które dostarczasz, `entryType` i `keyType` określają typ wpisu, który zawiera Klasa, oraz typ klucza, który jest kojarzony z każdym wpisem. Ze względu na ograniczenie należy dostarczyć do `keyType` typu, który implementuje <xref:System.IComparable> .  
  
 Poniższy przykład kodu tworzy obiekt, który zawiera `String` wpisy i kojarzy `Integer` klucz z każdym z nich. `Integer`implementuje <xref:System.IComparable> i w związku z tym spełnia ograniczenie dotyczące `keyType` .  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 `Of`Słowo kluczowe może być używane w tych kontekstach:  
  
 [Class, instrukcja](class-statement.md)  
  
 [Delegate — Instrukcja](delegate-statement.md)  
  
 [Function, instrukcja](function-statement.md)  
  
 [Interface, instrukcja](interface-statement.md)  
  
 [Structure — Instrukcja](structure-statement.md)  
  
 [Sub, instrukcja](sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IComparable>
- [Lista typów](type-list.md)
- [Typy ogólne w Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [W](../modifiers/in-generic-modifier.md)
- [Określoną](../modifiers/out-generic-modifier.md)
