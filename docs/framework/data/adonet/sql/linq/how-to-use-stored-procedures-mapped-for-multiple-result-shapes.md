---
title: "Porady: Użyj procedur składowanych mapowane do wielu kształtów wyników"
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
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fde4dd9044ff2bc6d781d7ceafec2bde3df7e14d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="6c73f-102">Porady: Użyj procedur składowanych mapowane do wielu kształtów wyników</span><span class="sxs-lookup"><span data-stu-id="6c73f-102">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>
<span data-ttu-id="6c73f-103">Gdy procedura składowana może zwracać wiele kształtów wynik, zwracany typ nie silnie typizowaną do projekcji pojedynczego kształtu.</span><span class="sxs-lookup"><span data-stu-id="6c73f-103">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="6c73f-104">Mimo że [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] można wygenerować wszystkich typów możliwych projekcji, nie może znać kolejności, w której będą zwracane.</span><span class="sxs-lookup"><span data-stu-id="6c73f-104">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="6c73f-105">Natomiast tego scenariusza z procedur składowanych, które powodują powstanie wielu kształtów wynik sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="6c73f-105">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="6c73f-106">Aby uzyskać więcej informacji, zobacz [porady: użycie przechowywane procedury mapowane sekwencyjnych kształtów wynik](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="6c73f-106">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="6c73f-107"><xref:System.Data.Linq.Mapping.ResultTypeAttribute> Atrybut jest stosowany na procedury składowane, które zwracają wiele typów wyników, aby określić zestaw procedura może zwracać typów.</span><span class="sxs-lookup"><span data-stu-id="6c73f-107">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c73f-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c73f-108">Example</span></span>  
 <span data-ttu-id="6c73f-109">W poniższym przykładzie kodu SQL kształt wyniku zależy od danych wejściowych (`shape =1` lub `shape = 2`).</span><span class="sxs-lookup"><span data-stu-id="6c73f-109">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="6c73f-110">Nie wiadomo, projekcji, które zostaną zwrócone najpierw.</span><span class="sxs-lookup"><span data-stu-id="6c73f-110">You do not know which projection will be returned first.</span></span>  
  
```  
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="6c73f-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c73f-111">Example</span></span>  
 <span data-ttu-id="6c73f-112">Należy użyć podobny do następującego kodu, aby wykonać tę procedurę składowaną.</span><span class="sxs-lookup"><span data-stu-id="6c73f-112">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c73f-113">Należy użyć <xref:System.Data.Linq.IMultipleResults.GetResult%2A> wzorzec do uzyskania moduł wyliczający prawidłowego typu, na podstawie informacji z procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="6c73f-113">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="6c73f-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c73f-114">See Also</span></span>  
 [<span data-ttu-id="6c73f-115">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="6c73f-115">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
