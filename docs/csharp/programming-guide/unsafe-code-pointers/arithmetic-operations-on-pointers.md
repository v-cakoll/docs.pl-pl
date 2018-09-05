---
title: Operacje arytmetyczne na wskaźnikach (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: 3694699466f7a200eecd5eef85f60fa19f9584a8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542196"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a>Operacje arytmetyczne na wskaźnikach (Przewodnik programowania w języku C#)
W tym temacie omówiono przy użyciu operatorów arytmetycznych `+` i **-** do manipulowania wskaźników.  
  
> [!NOTE]
>  Nie można wykonać wszystkie operacje arytmetyczne na wskaźnikach typu void.  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a>Dodawanie i odejmowanie wartości numerycznych do i z wskaźników  
 Wartość zostanie dodana `n` typu [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długie](../../../csharp/language-reference/keywords/long.md), lub [ulong](../../../csharp/language-reference/keywords/ulong.md) na wskaźnik `p`, dowolnego typu z wyjątkiem `void*`. Wynik `p+n` jest wskaźnikiem wynikające z dodawania `n * sizeof(p) to the address of p`. Podobnie `p-n` jest wskaźnikiem wynikające z odjęcie `n * sizeof(p)` z adresu `p`.  
  
## <a name="subtracting-pointers"></a>Odjęcie wskaźników  
 Możliwe jest również odjęcie wskaźników tego samego typu. Wynik jest zawsze typu `long`. Na przykład jeśli `p1` i `p2` są wskaźnikami typu `pointer-type*`, następnie wyrażenie `p1-p2` powoduje:  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 Żadne wyjątki są generowane, gdy operacja arytmetyczna przepełnienia domeny wskaźnika, a wynik zależy od implementacji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

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
