---
title: "Porady: bezpośrednio wykonania polecenia SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9f87572b27cfca7cc1188ab0986dadcba7bb3e29
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-directly-execute-sql-commands"></a><span data-ttu-id="44e7e-102">Porady: bezpośrednio wykonania polecenia SQL</span><span class="sxs-lookup"><span data-stu-id="44e7e-102">How to: Directly Execute SQL Commands</span></span>
<span data-ttu-id="44e7e-103">Zakładając, że <xref:System.Data.Linq.DataContext> połączenia, można użyć <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> do wykonania polecenia SQL, które niezwracanie obiektów.</span><span class="sxs-lookup"><span data-stu-id="44e7e-103">Assuming a <xref:System.Data.Linq.DataContext> connection, you can use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to execute SQL commands that do not return objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44e7e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="44e7e-104">Example</span></span>  
 <span data-ttu-id="44e7e-105">Poniższy przykład powoduje, że serwer SQL do zwiększenia UnitPrice 1,00.</span><span class="sxs-lookup"><span data-stu-id="44e7e-105">The following example causes SQL Server to increase UnitPrice by 1.00.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="44e7e-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44e7e-106">See Also</span></span>  
 [<span data-ttu-id="44e7e-107">Instrukcje: Bezpośrednie wykonywanie zapytań SQL</span><span class="sxs-lookup"><span data-stu-id="44e7e-107">How to: Directly Execute SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)  
 [<span data-ttu-id="44e7e-108">Komunikacja z bazą danych</span><span class="sxs-lookup"><span data-stu-id="44e7e-108">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
