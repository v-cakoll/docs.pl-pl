---
title: "Zwraca część wspólną dwóch sekwencji zestawu"
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
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4ff65c310323f7505f00dc4a768869cac8226d25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="return-the-set-intersection-of-two-sequences"></a>Zwraca część wspólną dwóch sekwencji zestawu
Użyj <xref:System.Linq.Queryable.Intersect%2A> operatora, aby zwrócić zestaw część wspólną dwóch sekwencji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Queryable.Intersect%2A> do zwrócenia sekwencji wszystkich krajów, w których obie `Customers` i `Employees` na żywo.  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Intersect%2A> operacja jest także zdefiniowana tylko dla zestawów. Semantyka dla multisets jest niezdefiniowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Translacja Operator zapytania standardowe](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
