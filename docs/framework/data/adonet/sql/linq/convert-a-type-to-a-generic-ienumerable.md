---
title: Przekonwertować typem rodzajowym interfejsem IEnumerable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: e1d8036dd7ef4e1f59e2af46ac101135c39ef0c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360442"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a>Przekonwertować typem rodzajowym interfejsem IEnumerable
Użyj <xref:System.Linq.Enumerable.AsEnumerable%2A> być zwracany argument typu ogólnego `IEnumerable`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (przy użyciu domyślnego ogólnego `Query`) może spróbować skonwertować kwerendy do bazy danych SQL i wykonaj go na serwerze. Ale `where` klauzuli odwołuje się do metody zdefiniowanej przez użytkownika po stronie klienta (`isValidProduct`), którego nie można przekonwertować do bazy danych SQL.  
  
 Rozwiązanie jest określenie ogólnego po stronie klienta <xref:System.Collections.Generic.IEnumerable%601> implementacja `where` do zastąpienia ogólnego <xref:System.Linq.IQueryable%601>. W tym celu wywoływania <xref:System.Linq.Enumerable.AsEnumerable%2A> operatora.  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
