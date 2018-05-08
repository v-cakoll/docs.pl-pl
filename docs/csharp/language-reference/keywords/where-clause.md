---
title: Klauzula where (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: bc040e17f5c612b9fc43a9ef24fb6f15f0942b8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="where-clause-c-reference"></a>Klauzula where (odwołanie w C#)
`where` Klauzuli jest używany w wyrażeniu zapytania, aby określić, które elementy ze źródła danych zostaną zwrócone w wyrażeniu zapytania. Ma to zastosowanie warunek typu Boolean (*predykatu*) do każdego elementu źródłowego (odwołuje się zmienna zakresu) i zwraca te, dla których określony warunek jest spełniony. Wyrażenie pojedynczego zapytania mogą zawierać wiele `where` klauzule i jedną klauzulę może zawierać wiele zakresie predykatu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `where` klauzuli odfiltrowuje wszystkie liczby, z wyjątkiem tych, które są mniej niż 5. Jeśli usuniesz `where` klauzuli, wszystkie liczby ze źródła danych będą zwracane. Wyrażenie `num < 5` jest predykatu, która jest stosowana do każdego elementu.  
  
 [!code-csharp[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a>Przykład  
 W jednym `where` klauzuli, można określić dowolną liczbę predykaty odpowiednio przy użyciu [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) i [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md) operatorów. W poniższym przykładzie zapytanie określa dwa predykaty wybór liczby parzyste, które są mniej niż 5.  
  
 [!code-csharp[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a>Przykład  
 A `where` klauzula może zawierać jedną lub kilka metod, które zwracają wartości logiczne. W poniższym przykładzie `where` klauzuli używa metody w celu ustalenia, czy bieżąca wartość zmiennej zakresu jest parzysta lub nieparzysta.  
  
 [!code-csharp[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a>Uwagi  
 `where` Klauzula jest mechanizm filtrowania. Go może być umieszczony niemal z dowolnego miejsca w wyrażeniu zapytania z tym nie może być pierwszym lub ostatnim klauzuli. A `where` klauzula może występować przed lub po [grupy](../../../csharp/language-reference/keywords/group-clause.md) klauzuli w zależności od tego, czy masz do filtrowania elementów źródła przed lub po ich grupowania.  
  
 Jeśli określony predykat nie jest prawidłowy dla elementów w źródle danych, spowoduje błąd kompilacji. To korzyścią silnego typu sprawdzania pochodzącymi [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].  
  
 W czasie kompilacji `where` — słowo kluczowe jest konwertowany na wywołanie <xref:System.Linq.Enumerable.Where%2A> metody standardowe — Operator zapytań.  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe zapytania (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [from, klauzula](../../../csharp/language-reference/keywords/from-clause.md)  
 [select, klauzula](../../../csharp/language-reference/keywords/select-clause.md)  
 [Filtrowanie danych](../../programming-guide/concepts/linq/filtering-data.md)  
 [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Wprowadzenie do korzystania z LINQ w C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
