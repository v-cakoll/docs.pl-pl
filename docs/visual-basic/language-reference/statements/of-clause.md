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
ms.openlocfilehash: 9ace0ad55d9eb1618dbdafb0d49d1ff4b169a877
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="of-clause-visual-basic"></a>Of — Klauzula (Visual Basic)
Wprowadza `Of` klauzuli, która identyfikuje *parametr typu* na *ogólnego* klasy, struktury, interfejsu, delegata lub procedury. Informacje o typach ogólny, zobacz [typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## <a name="using-the-of-keyword"></a>Przy użyciu słowa kluczowego  
 Poniższy przykład kodu wykorzystuje `Of` — słowo kluczowe do zdefiniowania konturu klasy, która przyjmuje dwa parametry typu. On *ogranicza* `keyType` parametru przez <xref:System.IComparable> interfejsu, co oznacza, że kod odbierającą należy podać argument typu, który implementuje <xref:System.IComparable>. Jest to konieczne, aby `add` można wywołać procedury <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> metody. Aby uzyskać więcej informacji dotyczących ograniczeń, zobacz [lista typów](../../../visual-basic/language-reference/statements/type-list.md).  
  
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
  
 Po wykonaniu powyższych definicji klasy można utworzyć różne `dictionary` klasy z niego. Typy informacyjnym `entryType` i `keyType` ustalić, jakiego typu wpisu klasy przechowuje i jakiego typu klucza kojarzy z każdego wpisu. Ze względu na ograniczenia, należy podać do `keyType` typu, który implementuje <xref:System.IComparable>.  
  
 Poniższy przykład kodu tworzy obiekt przechowujący `String` wpisy i skojarzone `Integer` kluczy z każdej z nich. `Integer` implementuje <xref:System.IComparable> i w związku z tym spełnia ograniczenia na `keyType`.  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 Instrukcja `Of` <słowo kluczowe> może być używana w następujących kontekstach:  
  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IComparable>  
 [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [limit](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
