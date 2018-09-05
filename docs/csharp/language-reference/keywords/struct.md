---
title: struct (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 7931da2e5f5c493b54eb1f33a1d6f57b38592f6e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530195"
---
# <a name="struct-c-reference"></a>struct (odwołanie w C#)
A `struct` typ jest typem wartości, które jest zazwyczaj używany do hermetyzacji mniejszym grupom powiązanych zmiennych, takich jak współrzędnych prostokąta lub właściwości elementu w magazynie. Poniższy przykład przedstawia deklarację prostą strukturą:  
  
```csharp  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a>Uwagi  
 Struktury mogą także zawierać [konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md), [stałe](../../../csharp/programming-guide/classes-and-structs/constants.md), [pola](../../../csharp/programming-guide/classes-and-structs/fields.md), [metody](../../../csharp/programming-guide/classes-and-structs/methods.md), [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md), [indeksatory](../../../csharp/programming-guide/indexers/index.md), [operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [zdarzenia](../../../csharp/programming-guide/events/index.md), i [zagnieżdżone typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md), chociaż Jeśli kilka takich elementów członkowskich są wymagane, możesz należy wziąć pod uwagę klasy jako możliwej do typu Twojej zamiast tego.  
  
 Aby uzyskać przykłady, zobacz [przy użyciu struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
 Struktury można zaimplementować interfejs, ale nie może dziedziczyć innej struktury. Z tego powodu składowe struktury nie można zadeklarować jako `protected`.  
  
 Aby uzyskać więcej informacji, zobacz [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## <a name="examples"></a>Przykłady  
 Aby uzyskać więcej informacji, zobacz [przy użyciu struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 Aby uzyskać przykłady, zobacz [przy użyciu struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md)  
- [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Typy](../../../csharp/language-reference/keywords/types.md)  
- [Typy wartości](../../../csharp/language-reference/keywords/value-types.md)  
- [class](../../../csharp/language-reference/keywords/class.md)  
- [interface](../../../csharp/language-reference/keywords/interface.md)  
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
