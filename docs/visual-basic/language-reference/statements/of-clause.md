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
ms.openlocfilehash: d88c43efe858d6b81b7d8d2470b234ff5d40632a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353841"
---
# <a name="of-clause-visual-basic"></a>Of — Klauzula (Visual Basic)
Wprowadza klauzulę `Of`, która identyfikuje *parametr typu* dla klasy *ogólnej* , struktury, interfejsu, delegata lub procedury. Aby uzyskać informacje na temat typów ogólnych, zobacz [typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Za pomocą słowa kluczowego  
 Poniższy przykład kodu używa słowa kluczowego `Of` do definiowania konspektu klasy, która przyjmuje dwa parametry typu. *Ogranicza* parametr `keyType` przez interfejs <xref:System.IComparable>, co oznacza, że kod zużywający musi dostarczyć argument typu, który implementuje <xref:System.IComparable>. Jest to konieczne, aby procedura `add` mogła wywołać metodę <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji o ograniczeniach, zobacz [Type list](../../../visual-basic/language-reference/statements/type-list.md).  
  
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
  
 Jeśli poprzednia definicja klasy zostanie ukończona, można utworzyć w niej wiele klas `dictionary`. Typy, które podasz, `entryType` i `keyType` określają typ wpisu, który zawiera Klasa, oraz typ klucza, który jest kojarzony z każdym wpisem. Ze względu na ograniczenie należy podać, aby `keyType` typ, który implementuje <xref:System.IComparable>.  
  
 Poniższy przykład kodu tworzy obiekt, który przechowuje `String` wpisy i kojarzy klucz `Integer` z każdym z nich. `Integer` implementuje <xref:System.IComparable> i w związku z tym spełnia ograniczenie `keyType`.  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 Słowa kluczowego `Of` można użyć w tych kontekstach:  
  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IComparable>
- [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Podczas](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Określoną](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
