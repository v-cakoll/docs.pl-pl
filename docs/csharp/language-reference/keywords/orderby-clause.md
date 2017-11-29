---
title: "Klauzula orderby (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc688e7ba164dcca71d13b2d79d30f1373c4778e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="orderby-clause-c-reference"></a>Klauzula orderby (odwołanie w C#)
W wyrażeniu zapytania `orderby` klauzuli powoduje, że zwrócony sekwencji lub podsekwencji (grupa) mają być sortowane w kolejności rosnącej lub malejącej. Można określić wiele kluczy w celu wykonywania operacji dodatkowej sortowania jeden lub więcej. Sortowanie jest wykonywane przez domyślna funkcja porównująca dla typu elementu. Domyślna kolejność sortowania jest rosnąca. Można również określić Niestandardowa funkcja porównująca. Jednak jest tylko dostępne przy użyciu składni oparte na metodzie. Aby uzyskać więcej informacji, zobacz [sortowanie danych](../../programming-guide/concepts/linq/sorting-data.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie słów w kolejności alfabetycznej, zaczynając od A sortuje pierwszego zapytania i drugiego zapytania sortuje te same wyrazy w kolejności malejącej. ( `ascending` — Słowo kluczowe jest wartością domyślną sortowania i można je pominąć.)  
  
 [!code-csharp[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje głównej sortowania na studentów nazwisk, a następnie dodatkowej sortowania na ich imiona.  
  
 [!code-csharp[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]  
  
## <a name="remarks"></a>Uwagi  
 W czasie kompilacji `orderby` klauzuli są tłumaczone na wywołanie <xref:System.Linq.Enumerable.OrderBy%2A> metody. Wiele kluczy w `orderby` klauzuli przełożyć na <xref:System.Linq.Enumerable.ThenBy%2A> wywołania metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Słowa kluczowe zapytania (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Group — klauzula](../../../csharp/language-reference/keywords/group-clause.md)  
 [Wprowadzenie do korzystania z LINQ w C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
