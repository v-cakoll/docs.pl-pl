---
title: void — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: ce52e4d19335db0e21637b87bbd1589c86c06ae1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660323"
---
# <a name="void-c-reference"></a>void (odwołanie w C#)

Gdy jest używana jako zwracany typ metody `void` Określa, że metoda nie zwraca wartości.

`void` nie jest dozwolona na liście parametrów metody. Metody, która nie przyjmuje żadnych parametrów i zwraca wartość nie jest zadeklarowana w następujący sposób:

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void` Umożliwia również w niebezpiecznym kontekście deklarowany jest wskaźnik do nieznanego typu. Aby uzyskać więcej informacji, zobacz [typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md).

`void` jest aliasem dla programu .NET Framework <xref:System.Void?displayProperty=nameWithType> typu.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy odwołań](reference-types.md)
- [Typy wartości](value-types.md)
- [Metody](../../programming-guide/classes-and-structs/methods.md)
- [Niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md)