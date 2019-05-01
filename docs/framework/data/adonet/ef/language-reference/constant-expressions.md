---
title: Wyrażenia stałe
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: 10c74ede8d490bf96a9d0855889669bdc2628b01
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785362"
---
# <a name="constant-expressions"></a><span data-ttu-id="f6702-102">Wyrażenia stałe</span><span class="sxs-lookup"><span data-stu-id="f6702-102">Constant Expressions</span></span>
<span data-ttu-id="f6702-103">Wyrażenie stałe składa się z wartością stałą.</span><span class="sxs-lookup"><span data-stu-id="f6702-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="f6702-104">Wartości stałe bezpośrednio są konwertowane na stałe polecenia drzewa wyrażeń, bez tłumaczenia na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="f6702-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="f6702-105">Obejmuje to stała wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f6702-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="f6702-106">W związku z tym, zachowanie źródła danych można się spodziewać dla wszystkich wyrażeń obejmujących stałe.</span><span class="sxs-lookup"><span data-stu-id="f6702-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="f6702-107">Może to spowodować, że zachowanie, które różni się od zachowania CLR.</span><span class="sxs-lookup"><span data-stu-id="f6702-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="f6702-108">Poniższy przykład pokazuje wyrażenie stałe, które jest oceniane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="f6702-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] <span data-ttu-id="f6702-109">nie obsługuje przy użyciu klasy użytkownika jako stała.</span><span class="sxs-lookup"><span data-stu-id="f6702-109">does not support using a user class as a constant.</span></span> <span data-ttu-id="f6702-110">Jednak odwołaniem do właściwości w klasie użytkownika jest uznawany za stałą, zostanie przekonwertowane na wyrażeniu stałym drzewa poleceń i wykonywane w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="f6702-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6702-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6702-111">See also</span></span>

- [<span data-ttu-id="f6702-112">Wyrażenia w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="f6702-112">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
