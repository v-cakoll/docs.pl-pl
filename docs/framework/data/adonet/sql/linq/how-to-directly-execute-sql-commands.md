---
title: 'Instrukcje: Bezpośrednie wykonywanie poleceń SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: 3f28351a29915bebd698e00113bb05647d8412b4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781997"
---
# <a name="how-to-directly-execute-sql-commands"></a>Instrukcje: Bezpośrednie wykonywanie poleceń SQL
Przy założeniu <xref:System.Data.Linq.DataContext.ExecuteCommand%2A>połączenia, można użyć do wykonywania poleceń SQL, które nie zwracają obiektów. <xref:System.Data.Linq.DataContext>  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje, że SQL Server zwiększyć wartość CenaJednostkowa o 1,00.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Bezpośrednie wykonywanie zapytań SQL](how-to-directly-execute-sql-queries.md)
- [Komunikacja z bazą danych](communicating-with-the-database.md)
