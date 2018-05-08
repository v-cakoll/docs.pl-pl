---
title: Pisanie zapytań LINQ w C#
description: Jak pisać zapytania.
ms.date: 12/1/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: a9683dbf3c4101829054477824ccc7135f20f535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="write-linq-queries-in-c"></a>Pisanie zapytań LINQ w C#

W tym temacie przedstawiono trzy sposoby, w których można napisać zapytanie LINQ w C#:  
  
1.  Należy użyć składni zapytania.  
  
2.  Należy użyć składni metody.  
  
3.  Użyj kombinacji składnia zapytania a składnia metody.  
  
 W poniższych przykładach pokazano kilka prostych zapytań LINQ za pomocą każdego z podejść wymienionych powyżej. Ogólnie rzecz biorąc reguła jest używana (1), jeśli to możliwe i (2) i (3), jeśli zajdzie potrzeba.  
  
> [!NOTE]
>  Kwerendy te działają na prosty kolekcje w pamięci; Podstawowa składnia jest jednak używaną w składniku LINQ to Entities i LINQ do XML.  
  
## <a name="example"></a>Przykład  
  
## <a name="query-syntax"></a>Składnia zapytania  
 Zalecanym sposobem zapisu większości kwerend jest użycie *Składnia kwerendy* utworzyć *wyrażenia zapytań*. W poniższym przykładzie przedstawiono trzy wyrażenia zapytania. Pierwsze wyrażenie zapytanie pokazuje, jak filtrowanie lub ograniczanie wyników, stosując warunków z `where` klauzuli. Zwraca wszystkie elementy w sekwencji źródłowej, w których wartości są większe niż 7 lub mniej niż 3. Drugie wyrażenie pokazano, jak kolejność zwracanych wyników. Trzeci wyrażenie pokazano, jak grupowanie wyników według klucza. Ta kwerenda zwraca dwie grupy oparte na pierwszą literę słowa.  
  
 [!code-csharp[csProgGuideLINQ#5](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]  
  
 Należy zauważyć, że typ zapytania <xref:System.Collections.Generic.IEnumerable%601>. Wszystkie te zapytania można można pisać przy użyciu `var` jak pokazano w poniższym przykładzie:  
  
 `var query = from num in numbers...`  
  
 W poprzednim przykładzie zapytania nie faktycznie wykonuj dopóki iteracja zmienną zapytania w `foreach` lub innych instrukcję. Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
## <a name="example"></a>Przykład  
  
## <a name="method-syntax"></a>Składnia metody  
 Niektóre operacje kwerend muszą być wyrażone jako wywołania metody. Najbardziej typowe metody te są tymi, które zwraca pojedyncze wartości liczbowe, takie jak <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>i tak dalej. Te metody zawsze należy wywołać ostatniego w każde zapytanie operacji ponieważ reprezentuje pojedynczą wartość i nie może służyć jako źródło dla operacji zapytania dodatkowe. W poniższym przykładzie pokazano wywołanie metody w wyrażeniu zapytania:  
  
 [!code-csharp[csProgGuideLINQ#6](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]  
  
## <a name="example"></a>Przykład  
 Jeśli metoda ma parametry akcji lub Func, te są udostępniane w formie [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) wyrażenia, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideLINQ#7](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]  
  
 W poprzednich zapytań tylko zapytania #4 wykonuje natychmiast. Jest to spowodowane zwraca pojedynczą wartość, a nie ogólnego <xref:System.Collections.Generic.IEnumerable%601> kolekcji. Tej metody ma używać `foreach` Aby obliczyć wartość.  
  
 Każdy z poprzednich zapytań można pisać przy użyciu niejawnego wpisaniu [var](../language-reference/keywords/var.md), jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideLINQ#8](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]  
  
## <a name="example"></a>Przykład  
  
## <a name="mixed-query-and-method-syntax"></a>Mieszane składnia zapytania i metody  
 W tym przykładzie pokazano, jak używać składni metody wyników klauzuli zapytania. Tylko ujmij wyrażenie kwerendy w nawiasy, a następnie zastosować operator kropki i wywołania metody. W poniższym przykładzie zapytanie #7 zwraca liczbę cyfr, którego wartość wynosi od 3 do 7. Ogólnie rzecz biorąc jednak warto użyć zmiennej drugi do przechowywania wyniku wywołania metody. W ten sposób zapytanie jest mniej prawdopodobne różni się od wyników zapytania.  
  
 [!code-csharp[csProgGuideLINQ#9](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]  
  
 Ponieważ zapytania #7 zwraca pojedynczą wartość i nie jest kolekcją, natychmiast wykonuje zapytania.  
  
 Poprzednie zapytanie można pisać przy użyciu niejawnego wpisaniu `var`w następujący sposób:  
  
```csharp  
var numCount = (from num in numbers...  
```  
  
 Go może być zapisany w składni metody w następujący sposób:  
  
```csharp  
var numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
 Może być zapisany przy użyciu wpisywać jawne, w następujący sposób:  
  
```csharp  
int numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
## <a name="see-also"></a>Zobacz też  
  [Wskazówki: Pisanie zapytań w języku C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [Wyrażenia zapytań LINQ](index.md)  
 [where, klauzula](../language-reference/keywords/where-clause.md)
