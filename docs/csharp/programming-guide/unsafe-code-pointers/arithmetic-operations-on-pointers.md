---
title: Operacje arytmetyczne na wskaźnikach - C# Programming Guide
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: bfa81bc926b4fe81455cecb88bc55f4dcd69268e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977841"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a>Operacje arytmetyczne na wskaźnikach (C# Programming Guide)
W tym temacie omówiono przy użyciu operatorów arytmetycznych `+` i `-` do manipulowania wskaźników.  
  
> [!NOTE]
>  Nie można wykonać wszystkie operacje arytmetyczne na wskaźnikach typu void.  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a>Dodawanie i odejmowanie wartości numerycznych do i z wskaźników  
 Wartość zostanie dodana `n` typu [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długie](../../../csharp/language-reference/keywords/long.md), lub [ulong](../../../csharp/language-reference/keywords/ulong.md) do wskaźnika. Jeśli `p` jest wskaźnikiem typu `pointer-type*`, wynik `p+n` jest wskaźnikiem wynikające z dodawania `n * sizeof(pointer-type)` adres `p`. Podobnie `p-n` jest wskaźnikiem wynikające z odjęcie `n * sizeof(pointer-type)` z adresu `p`.  
  
## <a name="subtracting-pointers"></a>Odjęcie wskaźników  
 Możliwe jest również odjęcie wskaźników tego samego typu. Wynik jest zawsze typu `long`. Na przykład jeśli `p1` i `p2` są wskaźnikami typu `pointer-type*`, następnie wyrażenie `p1-p2` powoduje:  
  
 `((long)p1 - (long)p2)/sizeof(pointer-type)`  
  
 Żadne wyjątki są generowane, gdy operacja arytmetyczna przepełnienia domeny wskaźnika, a wynik zależy od implementacji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuidePointers#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#14)]  
  
 [!code-csharp[csProgGuidePointers#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#15)]  
  
## <a name="c-language-specification"></a>specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
- [Manipulowanie wskaźnikami](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)
- [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
