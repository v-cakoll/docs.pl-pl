---
title: odwołanie typu C# void
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 465aaeadca603f14432478a7e5496a9ef4589ebe
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712861"
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

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy odwołań](reference-types.md)
- [Typy wartości](value-types.md)
- [Metody](../../programming-guide/classes-and-structs/methods.md)
- [Niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md)
