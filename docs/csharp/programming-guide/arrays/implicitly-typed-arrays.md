---
title: "Niejawnie wpisane tablice (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], implicity-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6e60ff600a04dab47e8b0ed52dda00441e17f25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a>Niejawnie wpisane tablice (Przewodnik programowania w języku C#)
Niejawnie wpisane tablicy, w którym jest wywnioskowany Typ wystąpienia tablicy można utworzyć z elementów wymienionych w inicjatorze tablicy. Zasady dla dowolnej zmiennej o typie określonym niejawnie dotyczą również niejawnie wpisane tablice. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Niejawnie wpisane tablice są zazwyczaj używane w wyrażeniach kwerend oraz typy anonimowe i inicjatory obiektów i kolekcji.  
  
 W poniższych przykładach pokazano, jak utworzyć tablicy o typie określonym niejawnie:  
  
 [!code-csharp[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]  
  
 W poprzednim przykładzie zwróć uwagę, że z niejawnie wpisane tablice nie nawiasy kwadratowe są używane po lewej stronie instrukcji inicjowania. Należy też zauważyć, że Tablice nieregularne są inicjowane przy użyciu `new []` podobnie jak tablice jednowymiarowej.  
  
## <a name="implicitly-typed-arrays-in-object-initializers"></a>Niejawnie wpisane tablice w inicjatorach obiektów  
 Po utworzeniu typu anonimowego, który zawiera tablicę tablicy musi niejawnie wpisanych w inicjatorze obiektu typu. W poniższym przykładzie `contacts` jest niejawnie wpisanych tablicę typy anonimowe, z których każdy zawiera tablicę o nazwie `PhoneNumbers`. Należy pamiętać, że `var` — słowo kluczowe nie jest używany wewnątrz inicjatory obiektów.  
  
 [!code-csharp[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)  
 [Tablice](../../../csharp/programming-guide/arrays/index.md)  
 [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [var](../../../csharp/language-reference/keywords/var.md)  
 [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
