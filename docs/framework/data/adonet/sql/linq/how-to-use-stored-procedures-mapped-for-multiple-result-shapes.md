---
title: 'Instrukcje: Używanie procedur składowanych zamapowanych na wiele kształtów wyników'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 406e44a0ee3b086ceb47b25a80c4fd0ff5a92607
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902658"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="67a1b-102">Instrukcje: Używanie procedur składowanych zamapowanych na wiele kształtów wyników</span><span class="sxs-lookup"><span data-stu-id="67a1b-102">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>
<span data-ttu-id="67a1b-103">Podczas procedury składowanej może zwrócić wielu kształtów wyników, zwracany typ nie silnie typizowane do projekcji pojedynczego kształtu.</span><span class="sxs-lookup"><span data-stu-id="67a1b-103">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="67a1b-104">Mimo że [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wygenerować wszystkich typów projekcji możliwe, nie wiedzieć, kolejność, w której zostanie zwrócony.</span><span class="sxs-lookup"><span data-stu-id="67a1b-104">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="67a1b-105">Natomiast tego scenariusza za pomocą procedur składowanych, które tworzą wielu kształtów wyników po kolei.</span><span class="sxs-lookup"><span data-stu-id="67a1b-105">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="67a1b-106">Aby uzyskać więcej informacji, zobacz [jak: Używanie procedur składowanych zmapowanych do sekwencyjnych kształtów wyników](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="67a1b-106">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="67a1b-107"><xref:System.Data.Linq.Mapping.ResultTypeAttribute> Atrybut jest stosowany do procedur przechowywanych, które zwraca wiele typów wyników do określenia zestawu typów, które może zwracać procedury.</span><span class="sxs-lookup"><span data-stu-id="67a1b-107">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67a1b-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="67a1b-108">Example</span></span>  
 <span data-ttu-id="67a1b-109">W poniższym przykładzie kodu SQL kształtu wynik zależy od danych wejściowych (`shape =1` lub `shape = 2`).</span><span class="sxs-lookup"><span data-stu-id="67a1b-109">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="67a1b-110">Nie wiesz, projekcji, które zostaną zwrócone najpierw.</span><span class="sxs-lookup"><span data-stu-id="67a1b-110">You do not know which projection will be returned first.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="67a1b-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="67a1b-111">Example</span></span>  
 <span data-ttu-id="67a1b-112">Aby wykonać tę procedurę składowaną należy użyć kodu podobnego do następującego.</span><span class="sxs-lookup"><span data-stu-id="67a1b-112">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67a1b-113">Należy użyć <xref:System.Data.Linq.IMultipleResults.GetResult%2A> wzorca, aby uzyskać moduł wyliczający odpowiedniego typu, w oparciu o swojej wiedzy na temat procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="67a1b-113">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="67a1b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67a1b-114">See also</span></span>

- [<span data-ttu-id="67a1b-115">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="67a1b-115">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
