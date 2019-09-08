---
title: 'Instrukcje: Ponowne użycie połączenia między poleceniem ADO.NET a DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: f1ee7726042327eae88e69e9e6d062909c5bc74e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793289"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>Instrukcje: Ponowne użycie połączenia między poleceniem ADO.NET a DataContext
Ponieważ [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jest częścią ADO.NET technologii i opiera się na usługach zapewnianych przez ADO.NET, można ponownie użyć połączenia między poleceniem ADO.NET <xref:System.Data.Linq.DataContext>a.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak ponownie użyć tego samego połączenia między poleceniem ADO.NET a <xref:System.Data.Linq.DataContext>.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](background-information.md)
- [ADO.NET i LINQ to SQL](ado-net-and-linq-to-sql.md)
- [Komunikacja z bazą danych](communicating-with-the-database.md)
