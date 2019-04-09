---
title: 'Instrukcje: Ponowne użycie połączenia między poleceniem ADO.NET a DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 47e1e45cfe693e3569c343f1058ce2d610af96dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163153"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>Instrukcje: Ponowne użycie połączenia między poleceniem ADO.NET a DataContext
Ponieważ [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jest częścią [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] rodziny technologii i zależy od usług udostępnianych przez [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], można ponownie użyć połączenia między [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] polecenia i <xref:System.Data.Linq.DataContext>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak ponownie użyć tego samego połączenia między [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] polecenia i <xref:System.Data.Linq.DataContext>.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [ADO.NET i LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)
- [Komunikacja z bazą danych](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
