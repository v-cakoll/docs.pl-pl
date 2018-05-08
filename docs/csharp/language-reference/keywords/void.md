---
title: void (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: e66efc287fc3ed0fcc15963a827fccb788c38753
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="void-c-reference"></a>void (odwołanie w C#)
Gdy jest używany jako typ zwracany metody, `void` Określa, że metoda nie zwraca wartości.

`void` nie jest dozwolona na liście parametrów metody. Metody, która nie przyjmuje żadnych parametrów i nie zwraca wartości jest zadeklarowany w następujący sposób:

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void` Umożliwia również w niebezpiecznym kontekście zadeklarować wskaźnika do nieznanego typu. Aby uzyskać więcej informacji, zobacz [typów wskaźnikowych](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).

`void` jest to alias dla programu .NET Framework <xref:System.Void?displayProperty=nameWithType> typu.

## <a name="c-language-specification"></a>Specyfikacja języka C#
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)  
 [Typy wartości](../../../csharp/language-reference/keywords/value-types.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
