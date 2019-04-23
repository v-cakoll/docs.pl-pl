---
title: Zwracanie lub pomijanie elementów w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: 885e6bc011041320a3dc7b17d84b2541bf030adf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168314"
---
# <a name="return-or-skip-elements-in-a-sequence"></a>Zwracanie lub pomijanie elementów w sekwencji
Użyj <xref:System.Linq.Queryable.Take%2A> operatora zwracają danej liczby elementów w sekwencji, a następnie pominąć resztę.  
  
 Użyj <xref:System.Linq.Queryable.Skip%2A> operator, aby pominąć danej liczby elementów w sekwencji, a następnie wróć resztę.  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> mają pewne ograniczenia, gdy są one używane w kwerendach do programu SQL Server 2000. Aby uzyskać więcej informacji, zobacz wpis "Pomiń i Pobierz wyjątki w programie SQL Server 2000 do niego dostępu" w [Rozwiązywanie problemów](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wykonuje translację <xref:System.Linq.Queryable.Skip%2A> przy użyciu podzapytania SQL `NOT EXISTS` klauzuli. Tłumaczenie ma następujące ograniczenia:  
  
-   Argument musi być ustawiony. Multisets nie są obsługiwane, nawet wtedy, gdy określona.  
  
-   Wygenerowane zapytanie może być znacznie bardziej skomplikowane niż zapytanie wygenerowane dla podstawowego zapytania, na którym <xref:System.Linq.Queryable.Skip%2A> jest stosowany. Taki poziom złożoności może spowodować spadek wydajności lub nawet limitu czasu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Take` zaznacz pierwsze pięć `Employees` zatrudnienia. Należy zauważyć, że kolekcja jest najpierw posortowane według `HireDate`.  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Linq.Queryable.Skip%2A> zaznacz wszystkie regiony z wyjątkiem 10 najbardziej kosztowne `Products`.  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład łączy <xref:System.Linq.Queryable.Skip%2A> i <xref:System.Linq.Queryable.Take%2A> metody w celu pominięcia 50 pierwszych rekordów, a następnie wróć dalej 10.  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <xref:System.Linq.Queryable.Take%2A> i <xref:System.Linq.Queryable.Skip%2A> operacje są dobrze zdefiniowane wyłącznie w odniesieniu do uporządkowanej zestawów. Semantyka nieuporządkowane zestawy lub multisets jest niezdefiniowane.  
  
 Ze względu na ograniczenia w kolejności w programie SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spróbuje przenieść porządkowanie argument <xref:System.Linq.Queryable.Take%2A> lub <xref:System.Linq.Queryable.Skip%2A> operatora wynik operatora.  
  
> [!NOTE]
>  Tłumaczenie różni się [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] i [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)]. Jeśli planujesz używać <xref:System.Linq.Queryable.Skip%2A> z zapytaniem o dowolnej złożoności, należy użyć [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].  
  
 Należy wziąć pod uwagę następujące [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wyszukiwać [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Przenosi, to porządkowanie-to-end w języku SQL w następujący sposób:  
  
```  
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 Gdy <xref:System.Linq.Queryable.Take%2A> i <xref:System.Linq.Queryable.Skip%2A> są połączone, wszystkie określonej kolejności, muszą być zgodne. W przeciwnym wypadku wyniki są niezdefiniowane.  
  
 Do nieujemnej wartości, stałe argumentów całkowitych na podstawie SQL specyfikacji, zarówno <xref:System.Linq.Queryable.Take%2A> i <xref:System.Linq.Queryable.Skip%2A> są dobrze zdefiniowane.  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Translacja standardowego operatora zapytania](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
