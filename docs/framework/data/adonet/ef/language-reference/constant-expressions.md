---
title: Wyrażenia stałe
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: cc3a214a2faa06c79ee0794b0158381bff0c4b0b
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539883"
---
# <a name="constant-expressions"></a><span data-ttu-id="cbdbc-102">Wyrażenia stałe</span><span class="sxs-lookup"><span data-stu-id="cbdbc-102">Constant Expressions</span></span>
<span data-ttu-id="cbdbc-103">Wyrażenie stałe składa się z wartością stałą.</span><span class="sxs-lookup"><span data-stu-id="cbdbc-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="cbdbc-104">Wartości stałe bezpośrednio są konwertowane na stałe polecenia drzewa wyrażeń, bez tłumaczenia na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="cbdbc-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="cbdbc-105">Obejmuje to stała wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="cbdbc-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="cbdbc-106">W związku z tym, zachowanie źródła danych można się spodziewać dla wszystkich wyrażeń obejmujących stałe.</span><span class="sxs-lookup"><span data-stu-id="cbdbc-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="cbdbc-107">Może to spowodować, że zachowanie, które różni się od zachowania CLR.</span><span class="sxs-lookup"><span data-stu-id="cbdbc-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="cbdbc-108">Poniższy przykład pokazuje wyrażenie stałe, które jest oceniane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="cbdbc-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="cbdbc-109">Składnik LINQ to Entities nie obsługuje używania klasy użytkownika jako stała.</span><span class="sxs-lookup"><span data-stu-id="cbdbc-109">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="cbdbc-110">Jednak odwołaniem do właściwości w klasie użytkownika jest uznawany za stałą, zostanie przekonwertowane na wyrażeniu stałym drzewa poleceń i wykonywane w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="cbdbc-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbdbc-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbdbc-111">See also</span></span>

- [<span data-ttu-id="cbdbc-112">Wyrażenia w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="cbdbc-112">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
