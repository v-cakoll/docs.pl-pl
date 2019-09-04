---
title: Wyrażenia stałe
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: b31cd881f1307ec734c026d3c873d7a650e19a20
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251132"
---
# <a name="constant-expressions"></a><span data-ttu-id="ef133-102">Wyrażenia stałe</span><span class="sxs-lookup"><span data-stu-id="ef133-102">Constant Expressions</span></span>
<span data-ttu-id="ef133-103">Wyrażenie stałe składa się z stałej wartości.</span><span class="sxs-lookup"><span data-stu-id="ef133-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="ef133-104">Stałe wartości są bezpośrednio konwertowane na stałe wyrażenia drzewa poleceń, bez żadnego tłumaczenia na klienta.</span><span class="sxs-lookup"><span data-stu-id="ef133-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="ef133-105">Obejmuje to wyrażenia, które powodują powstanie wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="ef133-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="ef133-106">W związku z tym należy oczekiwać zachowania źródła danych dla wszystkich wyrażeń obejmujących stałe.</span><span class="sxs-lookup"><span data-stu-id="ef133-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="ef133-107">Może to spowodować zachowanie, które różni się od zachowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ef133-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="ef133-108">Poniższy przykład przedstawia wyrażenie stałe, które jest oceniane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="ef133-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="ef133-109">LINQ to Entities nie obsługuje używania klasy użytkownika jako stałej.</span><span class="sxs-lookup"><span data-stu-id="ef133-109">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="ef133-110">Jednak odwołanie do właściwości w klasie użytkownika jest uznawane za stałe i zostanie przekonwertowane na wyrażenie stałe drzewa poleceń i wykonane w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="ef133-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef133-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef133-111">See also</span></span>

- [<span data-ttu-id="ef133-112">Wyrażenia w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="ef133-112">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
