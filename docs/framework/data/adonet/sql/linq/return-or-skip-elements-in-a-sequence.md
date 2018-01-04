---
title: "Zwracanym lub Pomiń elementy w sekwencji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d588ad393d6077d5b6e5279a1212f69da9a7d64c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="return-or-skip-elements-in-a-sequence"></a>Zwracanym lub Pomiń elementy w sekwencji
Użyj <xref:System.Linq.Queryable.Take%2A> operatora w celu uzyskania danej liczby elementów w sekwencji, a następnie pominąć resztę.  
  
 Użyj <xref:System.Linq.Queryable.Skip%2A> operatora, aby pominąć danej liczby elementów w sekwencji, a następnie wróć resztę.  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A>i <xref:System.Linq.Enumerable.Skip%2A> mają pewne ograniczenia, gdy są one używane w kwerendach do programu SQL Server 2000. Aby uzyskać więcej informacji, zobacz wpis "Pomiń i podjąć wyjątków w programie SQL Server 2000" w [Rozwiązywanie problemów](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]wykonuje translację <xref:System.Linq.Queryable.Skip%2A> za pomocą podzapytania SQL `NOT EXISTS` klauzuli. Tłumaczenie ma następujące ograniczenia:  
  
-   Argument musi być ustawiony. Multisets nie są obsługiwane, nawet jeśli uporządkowane.  
  
-   Wygenerowane zapytanie może być znacznie bardziej skomplikowane niż zapytania wygenerowany dla zapytania bazowego, na którym <xref:System.Linq.Queryable.Skip%2A> została zastosowana. Taki poziom złożoności może spowodować spadek wydajności lub nawet limitu czasu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Take` Wybierz pierwsze pięć `Employees` dzierżawione. Należy pamiętać, że kolekcja jest najpierw posortowane według `HireDate`.  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Linq.Queryable.Skip%2A> aby wybrać wszystkie z wyjątkiem 10 najdroższych `Products`.  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład łączy <xref:System.Linq.Queryable.Skip%2A> i <xref:System.Linq.Queryable.Take%2A> metody Pomiń pierwsze 50 rekordów, a następnie wróć dalej 10.  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <xref:System.Linq.Queryable.Take%2A>i <xref:System.Linq.Queryable.Skip%2A> operacje są jasno określone tylko względem uporządkowane zestawy. Semantyka nieuporządkowaną zestawów lub multisets jest niezdefiniowana.  
  
 Ze względu na ograniczenia dotyczące kolejności w programie SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] próbuje przenieść kolejność argument <xref:System.Linq.Queryable.Take%2A> lub <xref:System.Linq.Queryable.Skip%2A> operatora wynik operatora.  
  
> [!NOTE]
>  Tłumaczenie jest różne dla [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] i [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)]. Jeśli planujesz używać <xref:System.Linq.Queryable.Skip%2A> z zapytaniem żadnych złożoności, użyj [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].  
  
 Należy rozważyć [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kwerendy [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Przenosi kolejności w celu w języku SQL w następujący sposób:  
  
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
  
 Gdy <xref:System.Linq.Queryable.Take%2A> i <xref:System.Linq.Queryable.Skip%2A> są połączone, wszystkie określona kolejność muszą być zgodne. W przeciwnym razie wyniki są niezdefiniowane.  
  
 Dla nieujemną, stałych argumentów całkowitych oparte na specyfikacji SQL zarówno <xref:System.Linq.Queryable.Take%2A> i <xref:System.Linq.Queryable.Skip%2A> są dobrze zdefiniowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Translacja standardowego operatora zapytania](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
