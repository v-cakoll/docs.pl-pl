---
title: "void (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords: void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a71cac30132417abce60cdde54322b5f2067d39d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="void-c-reference"></a>void (odwołanie w C#)
Gdy jest używany jako typ zwracany metody, `void` Określa, że metoda nie zwraca wartości.

`void`nie jest dozwolona na liście parametrów metody. Metody, która nie przyjmuje żadnych parametrów i nie zwraca wartości jest zadeklarowany w następujący sposób:

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void`Umożliwia również w niebezpiecznym kontekście zadeklarować wskaźnika do nieznanego typu. Aby uzyskać więcej informacji, zobacz [typów wskaźnikowych](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).

`void`jest to alias dla programu .NET Framework <xref:System.Void?displayProperty=nameWithType> typu.

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
