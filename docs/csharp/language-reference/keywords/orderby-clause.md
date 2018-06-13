---
title: Klauzula orderby (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: 1fd0036e8bd3c838fe92ca27635cd7638d59ef1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268058"
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
 [group, klauzula](../../../csharp/language-reference/keywords/group-clause.md)  
 [Wprowadzenie do korzystania z LINQ w C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
