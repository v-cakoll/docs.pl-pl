---
title: Konwertowanie typu na ogólny interfejs IEnumerable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: d75c9b9123b52b3e241bea1bbd1d302c406715e8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190383"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a>Konwertowanie typu na ogólny interfejs IEnumerable
Użyj <xref:System.Linq.Enumerable.AsEnumerable%2A> być zwracany argument wpisanych w formie ogólnego `IEnumerable`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (przy użyciu domyślnego ogólnego `Query`) spróbuje przekonwertować kwerendy do bazy danych SQL, a następnie uruchomić go na serwerze. Ale `where` klauzuli odwołuje się do metody zdefiniowanej przez użytkownika po stronie klienta (`isValidProduct`), której nie można skonwertować do bazy danych SQL.  
  
 To rozwiązanie jest określenie ogólnego klienta <xref:System.Collections.Generic.IEnumerable%601> implementacji `where` do zastąpienia ogólnego <xref:System.Linq.IQueryable%601>. Można to zrobić, wywołując <xref:System.Linq.Enumerable.AsEnumerable%2A> operatora.  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
