---
title: var (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: c311993ebcc5b5072959b2e79242bcdabd6de913
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="var-c-reference"></a>var (odwołanie w C#)
Począwszy od programu Visual C# 3.0, zmienne, które są zadeklarowane w zakresie metody może mieć niejawna "type" `var`. Niejawnie wpisane zmienna lokalna jest silnie typizowane, tak jakby użytkownik typ ma zadeklarowany, ale kompilator Określa typ. Deklaracje następujące dwa `i` działają tak samo:  
  
```csharp  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) i [relacje typu w operacjach zapytań LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwa wyrażenia zapytania. W pierwszym wyrażeniu stosowania `var` jest dozwolone, ale nie jest wymagana, ponieważ typ wyniku zapytania można jawnie określone jako `IEnumerable<string>`. Jednak w drugie wyrażenie `var` umożliwia wynik, który ma być kolekcją typów anonimowych i nazwę tego typu nie jest dostępny z wyjątkiem do samej siebie kompilatora. Użycie `var` nie ma konieczności Utwórz nową klasę dla wyniku. Należy pamiętać, że w przykładzie #2 `foreach` zmiennej iteracji `item` musi również być niejawnie wpisanych.  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Jawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
