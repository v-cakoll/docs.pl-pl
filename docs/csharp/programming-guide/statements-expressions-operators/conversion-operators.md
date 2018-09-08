---
title: Operatory konwersji (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
ms.openlocfilehash: cbf6a83d43a1b3a69e82a35d5d0875f62422cd3f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183317"
---
# <a name="conversion-operators-c-programming-guide"></a>Operatory konwersji (Przewodnik programowania w języku C#)
C# umożliwia programistom deklarowania konwersje na klasy lub struktury, tak aby klasy lub struktury mogą być konwertowane do lub z innych klas lub struktur lub typy podstawowe. Konwersje są zdefiniowane like — operatory i są nazywane dla typu, do którego konwertują. Typ argumentu, który ma zostać przekonwertowany lub typ wyniku konwersji, ale nie obu musi być typu zawierającego.  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a>Omówienie operatorów konwersji  
 Operatory konwersji mają następujące właściwości:  
  
-   Konwersje zadeklarowane jako `implicit` wykonywane automatycznie, gdy jest to wymagane.  
  
-   Konwersje zadeklarowane jako `explicit` wymaga rzutowania do wywołania.  
  
-   Wszystkie konwersje musi być zadeklarowany jako `static`.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Informacje dodatkowe:  
  
-   [Używanie operatorów konwersji](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [Rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [explicit](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [implicit](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [static](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Convert>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Tworzenie łańcucha zdefiniowanych przez użytkownika Konwersje jawne w języku C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
