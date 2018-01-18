---
title: "Wyrażenia stałe"
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
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 328284ce07a0361dbfd25b0d765000b497156ff7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="constant-expressions"></a><span data-ttu-id="11d73-102">Wyrażenia stałe</span><span class="sxs-lookup"><span data-stu-id="11d73-102">Constant Expressions</span></span>
<span data-ttu-id="11d73-103">Wyrażenie stałe składa się z wartością stałą.</span><span class="sxs-lookup"><span data-stu-id="11d73-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="11d73-104">Wartości stałe bezpośrednio są konwertowane na wyrażenia drzewa polecenia stałe, bez tłumaczenia na kliencie.</span><span class="sxs-lookup"><span data-stu-id="11d73-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="11d73-105">W tym wyrażeń, które powodują powstanie wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="11d73-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="11d73-106">W związku z tym zachowanie źródła danych można się spodziewać dla wszystkich wyrażeń zawierających stałe.</span><span class="sxs-lookup"><span data-stu-id="11d73-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="11d73-107">Może to spowodować zachowanie różni się od zachowania CLR.</span><span class="sxs-lookup"><span data-stu-id="11d73-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="11d73-108">W poniższym przykładzie przedstawiono stałe wyrażenie, które jest obliczane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="11d73-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="11d73-109">nie obsługuje używania klasy użytkownika jako stała.</span><span class="sxs-lookup"><span data-stu-id="11d73-109"> does not support using a user class as a constant.</span></span> <span data-ttu-id="11d73-110">Jednak odwołania do właściwości klasy użytkownika jest uznawany za stałą i będzie można przekonwertować na stałe wyrażenie drzewa polecenia ani wykonywać w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="11d73-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d73-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11d73-111">See Also</span></span>  
 [<span data-ttu-id="11d73-112">Wyrażenia w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="11d73-112">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
