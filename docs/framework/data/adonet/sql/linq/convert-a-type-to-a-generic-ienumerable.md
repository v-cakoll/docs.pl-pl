---
title: Konwertowanie typu na ogólny interfejs IEnumerable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: c92f65c22fe4b4128a171c757bb9e9c0ccbc3fee
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247731"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a>Konwertowanie typu na ogólny interfejs IEnumerable
Użyj <xref:System.Linq.Enumerable.AsEnumerable%2A> , aby zwrócić argument, który jest typem `IEnumerable`ogólnym.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (przy użyciu domyślnego generycznego `Query`) próba konwersji zapytania na SQL i wykonania go na serwerze. Natomiast klauzula odwołuje się do zdefiniowanej przez użytkownika metody po stronie`isValidProduct`klienta (), której nie można przekonwertować na SQL. `where`  
  
 Rozwiązaniem jest określenie, że <xref:System.Collections.Generic.IEnumerable%601> `where` implementacja ogólna po stronie klienta zastąpi ogólny <xref:System.Linq.IQueryable%601>. W tym celu należy wycofać <xref:System.Linq.Enumerable.AsEnumerable%2A> operatora.  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](query-examples.md)
