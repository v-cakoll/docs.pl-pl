---
title: Zwracanie zestawu różnic między dwoma sekwencjami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 92513ed33e2afb785edbdd462ba7bc14923aa6b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781145"
---
# <a name="return-the-set-difference-between-two-sequences"></a>Zwracanie zestawu różnic między dwoma sekwencjami
<xref:System.Linq.Queryable.Except%2A> Użyj operatora, aby zwrócić różnicę zestawu między dwiema sekwencjami.  
  
## <a name="example"></a>Przykład  
 Ten przykład używa <xref:System.Linq.Queryable.Except%2A> do zwracania sekwencji wszystkich krajów/regionów, w których `Customers` Live, ale w których nie `Employees` ma na żywo.  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 W programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]operacjajestrównieżzdefiniowana tylkodlazestawów.<xref:System.Linq.Queryable.Except%2A> Semantyka dla wielozestawów jest niezdefiniowana.  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](query-examples.md)
- [Translacja standardowego operatora zapytania](standard-query-operator-translation.md)
