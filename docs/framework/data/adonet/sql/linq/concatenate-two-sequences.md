---
title: "Łączenie dwóch sekwencji"
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
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e7230e1f53f58f37dacbb1f22fbad1593768e01e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="concatenate-two-sequences"></a>Łączenie dwóch sekwencji
Użyj <xref:System.Linq.Queryable.Concat%2A> operator do łączenia dwóch sekwencji.  
  
 <xref:System.Linq.Queryable.Concat%2A> Operator jest zdefiniowany dla uporządkowanych multisets gdzie zamówień odbiornika i argument są takie same.  
  
 Kolejność w programie SQL jest ostatnim krokiem przed wyniki są tworzone. Z tego powodu <xref:System.Linq.Queryable.Concat%2A> operator jest implementowane za pomocą `UNION ALL` i kolejność jej argumenty nie zostaną zachowane. Aby upewnić się, że porządkowania jest prawidłowa w wynikach, upewnij się, że jawnie kolejność wyników.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Queryable.Concat%2A> do zwrócenia sekwencji wszystkich `Customer` i `Employee` numerem telefonu i faksu.  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Queryable.Concat%2A> do zwrócenia sekwencji wszystkich `Customer` i `Employee` nazwy i mapowania numeru telefonu.  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Translacja Operator zapytania standardowe](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
