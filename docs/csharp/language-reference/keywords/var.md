---
title: var (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ab49a4f4fcbc990a1fd21139397d70fa9fbf5dd8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393851"
---
# <a name="var-c-reference"></a>var (odwołanie w C#)
Począwszy od Visual C# 3.0, zmienne, które są zadeklarowane w zakresie metoda może mieć niejawne "type" `var`. Niejawnie wpisane zmiennej lokalnej jest jednoznacznie określone typy, tak jak w przypadku możesz typu była zadeklarowana, ale kompilator Określa typ. Poniższe dwie deklaracje `i` są funkcjonalnie równoważne:  
  
```csharp  
var i = 10; // Implicitly typed. 
int i = 10; // Explicitly typed. 
```  
  
 Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) i [relacje typu w operacjach zapytań LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwa wyrażenia zapytania. W pierwszym wyrażeniu użytkowania `var` jest dozwolone, ale nie jest wymagana, ponieważ typ wyniku zapytania może być jawnie wyrażona jako `IEnumerable<string>`. Jednak w drugim wyrażeniu `var` umożliwia wynik, który ma być kolekcją typów anonimowych, i nazwę tego typu nie jest dostępny z wyjątkiem kompilatorowi sam. Korzystanie z `var` eliminuje konieczność Utwórz nową klasę dla wyniku. Należy pamiętać, że w przykładzie 2, `foreach` zmiennej iteracyjnej `item` również musi być wpisana niejawnie.  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Jawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
