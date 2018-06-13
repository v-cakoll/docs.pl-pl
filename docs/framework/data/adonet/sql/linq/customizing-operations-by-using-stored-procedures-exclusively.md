---
title: Wyłącznie Dostosowywanie operacje przy użyciu procedur składowanych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 3c60a9e430b4228117fd03a43a30f27342154b1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357517"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="cb431-102">Wyłącznie Dostosowywanie operacje przy użyciu procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="cb431-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>
<span data-ttu-id="cb431-103">Dostęp do danych za pomocą tylko procedury składowane jest typowym scenariuszem.</span><span class="sxs-lookup"><span data-stu-id="cb431-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb431-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb431-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="cb431-105">Opis</span><span class="sxs-lookup"><span data-stu-id="cb431-105">Description</span></span>  
 <span data-ttu-id="cb431-106">Można zmodyfikować w przykładzie [Dostosowywanie operacji przez przy użyciu procedur składowanych](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) zamieniając wywołania metody, która opakowuje procedury składowanej nawet pierwszego zapytania (co powoduje, że dynamiczne wykonywania instrukcji SQL).</span><span class="sxs-lookup"><span data-stu-id="cb431-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="cb431-107">Załóżmy `CustomersByCity` to metoda, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cb431-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cb431-108">Kod</span><span class="sxs-lookup"><span data-stu-id="cb431-108">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="cb431-109">Poniższy kod wykonuje bez żadnych dynamiczne SQL.</span><span class="sxs-lookup"><span data-stu-id="cb431-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="cb431-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb431-110">See Also</span></span>  
 [<span data-ttu-id="cb431-111">Obowiązki dewelopera podczas zastępowania domyślnego zachowania</span><span class="sxs-lookup"><span data-stu-id="cb431-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
