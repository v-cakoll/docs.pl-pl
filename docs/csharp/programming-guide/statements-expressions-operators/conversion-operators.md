---
title: Operatory konwersji (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
ms.openlocfilehash: 97e93230658b5d1da676b029169b63bc9006ddb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334717"
---
# <a name="conversion-operators-c-programming-guide"></a>Operatory konwersji (Przewodnik programowania w języku C#)
C# umożliwia deweloperom zadeklarować konwersje klasy lub struktury, dzięki czemu mogą być konwertowane klasy lub struktury, aby lub z innych klas lub struktur lub typy podstawowe. Konwersje zdefiniowano like — operatory o nazwie dla typu, które umożliwiają one konwertowanie. Typ argumentu, który ma zostać przekonwertowany lub typ wyniku konwersji, ale nie oba musi być typu zawierającego.  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a>Omówienie operatorów konwersji  
 Operatory konwersji mieć następujące właściwości:  
  
-   Konwersje zadeklarowany jako `implicit` wykonywane automatycznie, gdy jest wymagane.  
  
-   Konwersje zadeklarowany jako `explicit` wymagają rzutowanie do wywołania.  
  
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
 <xref:System.Convert>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Tworzenie łańcucha zdefiniowane przez użytkownika Konwersje jawne w języku C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
