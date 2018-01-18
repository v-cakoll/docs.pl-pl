---
title: "Określić, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek"
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
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 29b9b79915e94ed1015c7869692647c10da58f60
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>Określić, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek
<xref:System.Linq.Enumerable.All%2A> Operator zwraca `true` , gdy wszystkie elementy w sekwencji spełniają warunek.  
  
 <xref:System.Linq.Queryable.Any%2A> Operator zwraca `true` Jeśli dowolny element w sekwencji spełnia warunek.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca sekwencję klientów, którzy mają co najmniej jednego zamówienia. `Where` / `where` Daje w wyniku klauzuli `true` Jeśli dany `Customer` ma jakiekolwiek `Order`.  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod Visual Basic Określa listę klientów, którzy nie dokonali zamówienia i zapewnia, że dla każdego klienta na tej liście podano nazwę kontaktu.  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie C# zwraca sekwencję klientów, których zamówień `ShipCity` rozpoczynające się od "C". Również zwracany obejmuje klientów, którzy mają żadnych zleceń. (Zgodnie z projektem <xref:System.Linq.Queryable.All%2A> operator zwraca `true` dla pustej sekwencji.) Klienci z żadnych zamówień są eliminowane w danych wyjściowych konsoli przy użyciu `Count` operatora.  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
