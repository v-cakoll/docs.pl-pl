---
title: "Sformułować sprzężenia i iloczyn wektorowy zapytania"
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
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5f652f25d04480afb3df1f623347eee23d3ed258
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="formulate-joins-and-cross-product-queries"></a>Sformułować sprzężenia i iloczyn wektorowy zapytania
Poniższe przykłady przedstawiają sposób łączenia wyniki z wielu tabel.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto obcego klucza nawigacji w `From` w klauzuli [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` klauzuli w języku C#) aby zaznaczyć wszystkich zleceń dla klientów w Londynie.  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto obcego klucza nawigacji w `Where` w klauzuli [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`where` klauzuli w języku C#) do filtrowania wyjście z akcji `Products` którego `Supplier` znajduje się w Stanach Zjednoczonych.  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto obcego klucza nawigacji w `From` w klauzuli [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` klauzuli w języku C#) do filtrowania dla pracowników w Seattle, a z listy ich terytorium.  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto obcego klucza nawigacji w `Select` w klauzuli [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzuli w języku C#) do filtrowania dla par pracownikom, gdy pracownik raporty do innych i gdzie jest taka sama zarówno pracowników `City`.  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] przykład wygląda dla wszystkich klientów i zamówień upewnia się, że zamówienia są dopasowane do klientów, a gwarantuje, że dla każdego klienta na tej liście podano nazwę kontaktu.  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jawnie łączy dwie tabele i projekty wyników z obu tabel.  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy sprzężenie jawnie trzy tabele i projekty wyniki każdego z nich.  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób osiągnięcia `LEFT OUTER JOIN` przy użyciu `DefaultIfEmpty()`. `DefaultIfEmpty()` Metoda zwraca wartość null, gdy ma nie `Order` dla `Employee`.  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a>Przykład  
 Następujące przykładowe projekty `let` wyniku w sprzężeniu wyrażenia.  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `join` za pomocą klucza złożonego.  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia `join` gdzie jednej stronie dopuszcza wartość null, a drugi nie.  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
