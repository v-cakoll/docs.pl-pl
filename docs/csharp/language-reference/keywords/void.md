---
title: odwołanie typu C# void
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 0624b547ee2586334ac35d366ae3c8dfd14963ee
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742761"
---
# <a name="void-c-reference"></a>void (odwołanie w C#)

Gdy jest używany jako zwracany typ dla metody, `void` określa, że metoda nie zwraca wartości.

`void` nie jest dozwolone na liście parametrów metody. Metoda, która nie przyjmuje parametrów i nie zwraca żadnej wartości jest zadeklarowana w następujący sposób:

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void` jest również używany w niebezpiecznym kontekście, aby zadeklarować wskaźnik do nieznanego typu. Aby uzyskać więcej informacji, zobacz [typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md).

`void` jest aliasem dla typu <xref:System.Void?displayProperty=nameWithType> .NET Framework.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy odwołań](reference-types.md)
- [Typy wartości](../builtin-types/value-types.md)
- [Metody](../../programming-guide/classes-and-structs/methods.md)
- [Niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md)
