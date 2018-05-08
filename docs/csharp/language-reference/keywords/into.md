---
title: into (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: 9bc7d50b77fe42861f92cc5bec946678d11d73d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="into-c-reference"></a>into (odwołanie w C#)
`into` Kontekstowe słowo kluczowe może służyć do tworzenia tymczasowego identyfikatora do przechowywania wyników [grupy](../../../csharp/language-reference/keywords/group-clause.md), [sprzężenia](../../../csharp/language-reference/keywords/join-clause.md) lub [wybierz](../../../csharp/language-reference/keywords/select-clause.md) klauzuli do nowego identyfikatora. Sam ten identyfikator może być generator zapytań dodatkowych poleceń. W przypadku używania w `group` lub `select` klauzuli, użyj nowego identyfikatora czasami nazywa się *kontynuacji*.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono użycie `into` — słowo kluczowe, aby włączyć tymczasowy identyfikator `fruitGroup` mającego wnioskowany typ `IGrouping`. Za pomocą identyfikatora, można wywołać <xref:System.Linq.Enumerable.Count%2A> metody dla każdej grupy i wybierz tylko tych grup, które zawierają co najmniej dwa wyrazy.  
  
 [!code-csharp[cscsrefQueryKeywords#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/into_1.cs)]  
  
 Korzystanie z `into` w `group` klauzuli jest konieczne tylko wtedy, gdy chcesz wykonać operacje kwerend dodatkowe w każdej grupie. Aby uzyskać więcej informacji, zobacz [klauzuli group](../../../csharp/language-reference/keywords/group-clause.md).  
  
 Na przykład użycie `into` w `join` klauzuli, zobacz [klauzuli join](../../../csharp/language-reference/keywords/join-clause.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe zapytania (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [group, klauzula](../../../csharp/language-reference/keywords/group-clause.md)
