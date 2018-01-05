---
title: "Zwraca złożenie dwóch sekwencji zestawu"
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
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a9f1ba281c1c7bd6a6a0d96746caa512c6c208b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="return-the-set-union-of-two-sequences"></a>Zwraca złożenie dwóch sekwencji zestawu
Użyj <xref:System.Linq.Queryable.Union%2A> operatora, aby zwrócić zestaw złożenie dwóch sekwencji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Queryable.Union%2A> do zwrócenia wszystkich krajów, w którym są albo sekwencji `Customers` lub `Employees`.  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Union%2A> operator jest zdefiniowany dla multisets jako nieuporządkowaną złączeniem multisets (efektywnie wynik `UNION ALL` klauzuli SQL).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Translacja standardowego operatora zapytania](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
