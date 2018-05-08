---
title: struct (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 5a4863bc93a115d14e791509f99b7b13bee9f68f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="struct-c-reference"></a>struct (odwołanie w C#)
A `struct` typem jest typ wartości, która jest zwykle używana w celu hermetyzacji małych grup zmienne pokrewne, takie jak współrzędne prostokąta lub właściwości elementu w magazynie. W poniższym przykładzie przedstawiono deklaracji struktury prosty:  
  
```  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a>Uwagi  
 Struktury mogą również zawierać [konstruktorów](../../../csharp/programming-guide/classes-and-structs/constructors.md), [stałe](../../../csharp/programming-guide/classes-and-structs/constants.md), [pola](../../../csharp/programming-guide/classes-and-structs/fields.md), [metody](../../../csharp/programming-guide/classes-and-structs/methods.md), [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md), [indeksatory](../../../csharp/programming-guide/indexers/index.md), [operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [zdarzenia](../../../csharp/programming-guide/events/index.md), i [zagnieżdżone typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md), ale jeśli kilka takich elementów są wymagane, możesz należy rozważyć, co danego typu, klasę zamiast tego.  
  
 Aby uzyskać przykłady, zobacz [przy użyciu struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
 Struktury można zaimplementować interfejsu, ale nie może dziedziczyć innego struktury. Z tego powodu elementy członkowskie struktury nie można zadeklarować jako `protected`.  
  
 Aby uzyskać więcej informacji, zobacz [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## <a name="examples"></a>Przykłady  
 Aby uzyskać więcej informacji, zobacz [przy użyciu struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 Aby uzyskać przykłady, zobacz [przy użyciu struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md)  
 [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [Typy wartości](../../../csharp/language-reference/keywords/value-types.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [interface](../../../csharp/language-reference/keywords/interface.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
