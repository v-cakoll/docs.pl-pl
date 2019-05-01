---
title: Of — Klauzula (Visual Basic)
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
ms.openlocfilehash: 880570c714292b0c11eef4e2cd4c4b410bb075f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784153"
---
# <a name="of-clause-visual-basic"></a>Of — Klauzula (Visual Basic)
Wprowadza `Of` klauzula, która identyfikuje *parametr typu* na *ogólny* klasy, struktury, interfejsu, delegata lub procedury. Aby uzyskać informacji na temat typów ogólnych, zobacz [typów ogólnych w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Za pomocą słowa kluczowego  
 Poniższy przykład kodu wykorzystuje `Of` — słowo kluczowe do zdefiniowania konturu klasę, która przyjmuje dwa parametry typu. Jego *ogranicza* `keyType` parametru przez <xref:System.IComparable> interfejsu, co oznacza, że kod konsumencki należy podać argument typu, który implementuje <xref:System.IComparable>. Jest to konieczne, aby `add` można wywołać procedury <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> metody. Aby uzyskać więcej informacji na temat ograniczeń, zobacz [lista typów](../../../visual-basic/language-reference/statements/type-list.md).  
  
```  
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
  
 Po wykonaniu poprzednich definicji klasy, można utworzyć szereg `dictionary` klas z niego. Typy użytkownika `entryType` i `keyType` ustalić, jakiego typu wejścia tej klasy przechowuje i jakiego rodzaju klucz kojarzy z każdego wpisu. Ze względu na ograniczenia, należy podać do `keyType` typu, który implementuje <xref:System.IComparable>.  
  
 Poniższy przykład kodu tworzy obiekt, który zawiera `String` wpisy i kojarzy `Integer` kluczy z każdej z nich. `Integer` implementuje <xref:System.IComparable> i w związku z tym spełnia ograniczenia na `keyType`.  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 Słowa kluczowego `Of` można używać w następujących kontekstach:  
  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IComparable>
- [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [W](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [limit](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
