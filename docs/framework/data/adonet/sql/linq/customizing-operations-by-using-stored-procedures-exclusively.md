---
title: "Wyłącznie Dostosowywanie operacje przy użyciu procedur składowanych"
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
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 075565570d8dccc9ebd41d4a8d56014f8bb0f039
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="18d6d-102">Wyłącznie Dostosowywanie operacje przy użyciu procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="18d6d-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>
<span data-ttu-id="18d6d-103">Dostęp do danych za pomocą tylko procedury składowane jest typowym scenariuszem.</span><span class="sxs-lookup"><span data-stu-id="18d6d-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18d6d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="18d6d-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="18d6d-105">Opis</span><span class="sxs-lookup"><span data-stu-id="18d6d-105">Description</span></span>  
 <span data-ttu-id="18d6d-106">Można zmodyfikować w przykładzie [Dostosowywanie operacji przez przy użyciu procedur składowanych](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) zamieniając wywołania metody, która opakowuje procedury składowanej nawet pierwszego zapytania (co powoduje, że dynamiczne wykonywania instrukcji SQL).</span><span class="sxs-lookup"><span data-stu-id="18d6d-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="18d6d-107">Załóżmy `CustomersByCity` to metoda, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="18d6d-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="18d6d-108">Kod</span><span class="sxs-lookup"><span data-stu-id="18d6d-108">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="18d6d-109">Poniższy kod wykonuje bez żadnych dynamiczne SQL.</span><span class="sxs-lookup"><span data-stu-id="18d6d-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="18d6d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18d6d-110">See Also</span></span>  
 [<span data-ttu-id="18d6d-111">Obowiązki dewelopera w Zastępowanie domyślnego zachowania</span><span class="sxs-lookup"><span data-stu-id="18d6d-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
