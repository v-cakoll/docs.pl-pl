---
title: "Operatory konwersji (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5277c1160c604ee56ff575df5bd603e115588d21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
  
-   [Porady: Implementowanie zdefiniowanych przez użytkownika konwersji struktur](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [jawne](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [niejawne](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [statyczne](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Convert>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Tworzenie łańcucha zdefiniowane przez użytkownika Konwersje jawne w języku C#](http://go.microsoft.com/fwlink/?LinkId=112384)
