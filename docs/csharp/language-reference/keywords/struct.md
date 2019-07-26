---
title: struct- C# Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 1f1c512e1995df07fc4b9e18e34a85119e270bda
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433783"
---
# <a name="struct-c-reference"></a>struct (odwołanie w C#)

`struct` Typ jest typem wartości, który zwykle jest używany do hermetyzowania małych grup powiązanych zmiennych, takich jak współrzędne prostokąta lub Charakterystyka elementu w spisie. Poniższy przykład pokazuje prostą deklarację struktury:

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a>Uwagi

Struktury mogą również zawierać [konstruktory](../../programming-guide/classes-and-structs/constructors.md), [stałe](../../programming-guide/classes-and-structs/constants.md), [pola](../../programming-guide/classes-and-structs/fields.md), [metody](../../programming-guide/classes-and-structs/methods.md), [Właściwości](../../programming-guide/classes-and-structs/properties.md), [indeksatory](../../programming-guide/indexers/index.md), [Operatory](../../programming-guide/statements-expressions-operators/operators.md), [zdarzenia](../../programming-guide/events/index.md)i [typy zagnieżdżone](../../programming-guide/classes-and-structs/nested-types.md), chociaż w przypadku wielu takich członków wymagane, należy rozważyć przeprowadzenie klasy w zamian.

Aby zapoznać się z przykładami, zobacz [using structs](../../programming-guide/classes-and-structs/using-structs.md).

Struktury mogą implementować interfejs, ale nie mogą dziedziczyć z innej struktury. Z tego powodu elementy członkowskie struktury nie mogą być deklarowane jako `protected`.

Aby uzyskać więcej informacji, zobacz [struktury](../../programming-guide/classes-and-structs/structs.md).

## <a name="examples"></a>Przykłady

Aby uzyskać przykłady i więcej informacji, zobacz [using struktury](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby zapoznać się z przykładami, zobacz [using structs](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Tabela wartości domyślnych](default-values-table.md)
- [Tabela typów wbudowanych](built-in-types-table.md)
- [Typy](types.md)
- [Typy wartości](value-types.md)
- [class](class.md)
- [interface](interface.md)
- [Klasy i struktury](../../programming-guide/classes-and-structs/index.md)
