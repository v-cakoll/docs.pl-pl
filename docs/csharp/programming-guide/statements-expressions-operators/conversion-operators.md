---
title: Operatory konwersji - C# Programming Guide
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
ms.openlocfilehash: 43e81a342377b155fafe26bd0430384cddad5fd4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608230"
---
# <a name="conversion-operators-c-programming-guide"></a>Operatory konwersji (C# Programming Guide)

C# umożliwia programistom deklarowania konwersje na klasy lub struktury, tak aby klasy lub struktury mogą być konwertowane do lub z innych klas lub struktur lub typy podstawowe. Konwersje są zdefiniowane like — operatory i są nazywane dla typu, do którego konwertują. Typ argumentu, który ma zostać przekonwertowany lub typ wyniku konwersji, ale nie obu musi być typu zawierającego.  
  
 [!code-csharp[csProgGuideStatements#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#10)]  
  
## <a name="conversion-operators-overview"></a>Omówienie operatorów konwersji

 Operatory konwersji mają następujące właściwości:  
  
- Konwersje zadeklarowane jako `implicit` wykonywane automatycznie, gdy jest to wymagane.  
  
- Konwersje zadeklarowane jako `explicit` wymaga rzutowania do wywołania.  
  
- Wszystkie konwersje musi być zadeklarowany jako `static`.  
  
## <a name="related-sections"></a>Sekcje pokrewne

 Informacje dodatkowe:  
  
- [Używanie operatorów konwersji](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
- [Rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
- [Instrukcje: Implementowanie zdefiniowanych przez użytkownika konwersji struktur](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
- [explicit](../../../csharp/language-reference/keywords/explicit.md)  
  
- [implicit](../../../csharp/language-reference/keywords/implicit.md)  
  
- [static](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Convert>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Tworzenie łańcucha zdefiniowanych przez użytkownika Konwersje jawne w języku C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
