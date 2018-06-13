---
title: implicit (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: 160d9f7c0d58abd685bf1d799b53cc96a26aebe8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215020"
---
# <a name="implicit-c-reference"></a>implicit (odwołanie w C#)
`implicit` — Słowo kluczowe służy do deklarowania niejawne typu zdefiniowanego przez użytkownika operatora konwersji. Użycia, aby włączyć niejawne konwersje między typu zdefiniowanego przez użytkownika i innego typu, jeśli jest gwarantowana konwersji, aby nie spowodować utratę danych.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 Eliminując niepotrzebnego rzutowania niejawne konwersje może poprawić czytelność kodu źródłowego. Jednak ponieważ niejawne konwersje nie wymagają programistów jawnie rzutowania z typu na drugi, należy uważać, aby uniknąć nieoczekiwanych wyników. Ogólnie rzecz biorąc operatory niejawnej konwersji należy nigdy nie zgłaszają wyjątki i nigdy nie utracić informacje, aby używać bezpiecznego bez świadomości programisty. Jeśli operator konwersji nie spełniają tych kryteriów, powinien być oznaczony `explicit`. Aby uzyskać więcej informacji, zobacz [przy użyciu operatorów konwersji](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)  
 [Operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md)  
 [Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
