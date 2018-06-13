---
title: Operacje arytmetyczne na wskaźnikach (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: c40b125e42649093aa1f1fe860a3e8f5d2690359
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324304"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a>Operacje arytmetyczne na wskaźnikach (Przewodnik programowania w języku C#)
W tym temacie omówiono przy użyciu operatorów arytmetycznych `+` i **-** do manipulowania wskaźników.  
  
> [!NOTE]
>  Nie można wykonać wszystkie operacje arytmetyczne na wskaźnikach void.  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a>Dodawanie i odejmowanie wartości liczbowe do lub z wskaźników  
 Można dodać wartość `n` typu [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długi](../../../csharp/language-reference/keywords/long.md), lub [ulong](../../../csharp/language-reference/keywords/ulong.md) do wskaźnika, `p`, dowolnego typu, z wyjątkiem `void*`. Wynik `p+n` wskaźnika wynikające z Dodawanie `n * sizeof(p) to the address of p`. Podobnie `p-n` wskaźnika wynikające z odjęcie `n * sizeof(p)` z adresu `p`.  
  
## <a name="subtracting-pointers"></a>Odejmowanie wskaźników  
 Można również odjąć wskaźniki tego samego typu. Wynik jest zawsze typu `long`. Na przykład jeśli `p1` i `p2` są wskaźnikami typu `pointer-type*`, następnie wyrażenie `p1-p2` wynikiem:  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 Żadne wyjątki są generowane, gdy domeny wskaźnika przepełnienie arytmetyczne operacji, a wynik zależy od implementacji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)  
 [Manipulowanie wskaźnikami](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
