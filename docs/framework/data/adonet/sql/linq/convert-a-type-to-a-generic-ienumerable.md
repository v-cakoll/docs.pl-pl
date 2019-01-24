---
title: Konwertowanie typu do ogólnego interfejsu IEnumerable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: d1f4c1c4a561c893b5846e6ae0b08b2d78c3589d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509600"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a>Konwertowanie typu do ogólnego interfejsu IEnumerable
Użyj <xref:System.Linq.Enumerable.AsEnumerable%2A> być zwracany argument wpisanych w formie ogólnego `IEnumerable`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (przy użyciu domyślnego ogólnego `Query`) spróbuje przekonwertować kwerendy do bazy danych SQL, a następnie uruchomić go na serwerze. Ale `where` klauzuli odwołuje się do metody zdefiniowanej przez użytkownika po stronie klienta (`isValidProduct`), której nie można skonwertować do bazy danych SQL.  
  
 To rozwiązanie jest określenie ogólnego klienta <xref:System.Collections.Generic.IEnumerable%601> implementacji `where` do zastąpienia ogólnego <xref:System.Linq.IQueryable%601>. Można to zrobić, wywołując <xref:System.Linq.Enumerable.AsEnumerable%2A> operatora.  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a>Zobacz także
- [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
