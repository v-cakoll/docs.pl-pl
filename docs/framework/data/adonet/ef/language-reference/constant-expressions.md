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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ccc54df7a69db8186c653afb415a5679b65ab50d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="constant-expressions"></a><span data-ttu-id="59846-102">Wyrażenia stałe</span><span class="sxs-lookup"><span data-stu-id="59846-102">Constant Expressions</span></span>
<span data-ttu-id="59846-103">Wyrażenie stałe składa się z wartością stałą.</span><span class="sxs-lookup"><span data-stu-id="59846-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="59846-104">Wartości stałe bezpośrednio są konwertowane na wyrażenia drzewa polecenia stałe, bez tłumaczenia na kliencie.</span><span class="sxs-lookup"><span data-stu-id="59846-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="59846-105">W tym wyrażeń, które powodują powstanie wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="59846-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="59846-106">W związku z tym zachowanie źródła danych można się spodziewać dla wszystkich wyrażeń zawierających stałe.</span><span class="sxs-lookup"><span data-stu-id="59846-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="59846-107">Może to spowodować zachowanie różni się od zachowania CLR.</span><span class="sxs-lookup"><span data-stu-id="59846-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="59846-108">W poniższym przykładzie przedstawiono stałe wyrażenie, które jest obliczane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="59846-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="59846-109">nie obsługuje używania klasy użytkownika jako stała.</span><span class="sxs-lookup"><span data-stu-id="59846-109"> does not support using a user class as a constant.</span></span> <span data-ttu-id="59846-110">Jednak odwołania do właściwości klasy użytkownika jest uznawany za stałą i będzie można przekonwertować na stałe wyrażenie drzewa polecenia ani wykonywać w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="59846-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59846-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59846-111">See Also</span></span>  
 [<span data-ttu-id="59846-112">Wyrażenia w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="59846-112">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
