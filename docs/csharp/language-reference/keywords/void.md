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
ms.openlocfilehash: 87ccc3a18f0956ffe800ae97598e621e5ca72480
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238380"
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
