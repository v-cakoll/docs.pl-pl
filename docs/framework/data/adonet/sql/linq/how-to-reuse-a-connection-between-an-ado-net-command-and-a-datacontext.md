---
title: 'Instrukcje: Ponowne użycie połączenia między poleceniem ADO.NET a DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 47e1e45cfe693e3569c343f1058ce2d610af96dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163153"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="4b1b7-102">Instrukcje: Ponowne użycie połączenia między poleceniem ADO.NET a DataContext</span><span class="sxs-lookup"><span data-stu-id="4b1b7-102">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>
<span data-ttu-id="4b1b7-103">Ponieważ [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jest częścią [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] rodziny technologii i zależy od usług udostępnianych przez [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], można ponownie użyć połączenia między [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] polecenia i <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="4b1b7-103">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] family of technologies and is based on services provided by [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], you can reuse a connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b1b7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b1b7-104">Example</span></span>  
 <span data-ttu-id="4b1b7-105">Poniższy przykład pokazuje, jak ponownie użyć tego samego połączenia między [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] polecenia i <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="4b1b7-105">The following example shows how to reuse the same connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4b1b7-106">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b1b7-106">See also</span></span>

- [<span data-ttu-id="4b1b7-107">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="4b1b7-107">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="4b1b7-108">ADO.NET i LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4b1b7-108">ADO.NET and LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)
- [<span data-ttu-id="4b1b7-109">Komunikacja z bazą danych</span><span class="sxs-lookup"><span data-stu-id="4b1b7-109">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
