---
title: Zwracanie zestawu części wspólnych dwóch sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 944d0b2efe1e74f901a493d1c3202d0f180d599d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792704"
---
# <a name="return-the-set-intersection-of-two-sequences"></a>Zwracanie zestawu części wspólnych dwóch sekwencji
<xref:System.Linq.Queryable.Intersect%2A> Użyj operatora, aby zwrócić zestaw przecięcia z dwiema sekwencjami.  
  
## <a name="example"></a>Przykład  
 Ten przykład używa <xref:System.Linq.Queryable.Intersect%2A> do zwracania sekwencji wszystkich krajów/regionów, w których zarówno `Customers` , jak `Employees` i na żywo.  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 W programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]operacjajestrównieżzdefiniowana tylkodlazestawów.<xref:System.Linq.Queryable.Intersect%2A> Semantyka dla wielozestawów jest niezdefiniowana.  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](query-examples.md)
- [Translacja standardowego operatora zapytania](standard-query-operator-translation.md)
