---
title: void (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 223db893dd42181c234d9a07c1a1c00af26f0c30
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275585"
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

`void` Umożliwia również w niebezpiecznym kontekście deklarowany jest wskaźnik do nieznanego typu. Aby uzyskać więcej informacji, zobacz [typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).

`void` jest aliasem dla programu .NET Framework <xref:System.Void?displayProperty=nameWithType> typu.

## <a name="c-language-specification"></a>Specyfikacja języka C#
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)  
- [Typy wartości](../../../csharp/language-reference/keywords/value-types.md)  
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
