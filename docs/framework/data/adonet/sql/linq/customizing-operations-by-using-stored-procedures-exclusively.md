---
title: Dostosowywanie operacji przy użyciu wyłącznie procedur składowanych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 61230ffc5cd055ee64de9d519cdfb4d76c856ca3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038054"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="d7cee-102">Dostosowywanie operacji przy użyciu wyłącznie procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="d7cee-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>
<span data-ttu-id="d7cee-103">Dostęp do danych przy użyciu wyłącznie procedur składowanych jest typowym scenariuszem.</span><span class="sxs-lookup"><span data-stu-id="d7cee-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7cee-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7cee-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d7cee-105">Opis</span><span class="sxs-lookup"><span data-stu-id="d7cee-105">Description</span></span>  
 <span data-ttu-id="d7cee-106">Możesz zmodyfikować przykładu w [Dostosowywanie operacje, przy użyciu procedur składowanych](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) , zastępując wywołania metody, która otacza procedury składowanej nawet pierwsze zapytanie (co powoduje, że dynamiczne wykonanie instrukcji SQL).</span><span class="sxs-lookup"><span data-stu-id="d7cee-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="d7cee-107">Załóżmy `CustomersByCity` jest metodą, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d7cee-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d7cee-108">Kod</span><span class="sxs-lookup"><span data-stu-id="d7cee-108">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="d7cee-109">Poniższy kod wykonuje bez żadnych dynamiczny język SQL.</span><span class="sxs-lookup"><span data-stu-id="d7cee-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d7cee-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7cee-110">See also</span></span>

- [<span data-ttu-id="d7cee-111">Obowiązki dewelopera podczas zastępowania domyślnego zachowania</span><span class="sxs-lookup"><span data-stu-id="d7cee-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
