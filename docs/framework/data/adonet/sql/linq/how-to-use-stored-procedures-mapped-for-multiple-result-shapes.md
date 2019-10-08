---
title: 'Instrukcje: używanie procedur składowanych mapowanych dla wielu kształtów wyników'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 065e866ec5937c4af31c0b1563a7582cb4112eba
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003270"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="8c4fa-102">Instrukcje: używanie procedur składowanych mapowanych dla wielu kształtów wyników</span><span class="sxs-lookup"><span data-stu-id="8c4fa-102">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>
<span data-ttu-id="8c4fa-103">Gdy procedura składowana może zwracać wiele kształtów wyników, typ zwracany nie może być jednoznacznie wpisany do pojedynczego kształtu projekcji.</span><span class="sxs-lookup"><span data-stu-id="8c4fa-103">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="8c4fa-104">Chociaż [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] może generować wszystkie możliwe typy projekcji, nie może on znać kolejności, w której zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="8c4fa-104">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="8c4fa-105">Ten scenariusz należy wykonać z procedurami składowanymi, które tworzą sekwencyjnie wiele kształtów wynikowych.</span><span class="sxs-lookup"><span data-stu-id="8c4fa-105">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="8c4fa-106">Aby uzyskać więcej informacji, zobacz [How to: use procedur składowanych mapowanych na sekwencyjne kształty wynikowe](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="8c4fa-106">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="8c4fa-107">Atrybut <xref:System.Data.Linq.Mapping.ResultTypeAttribute> jest stosowany do procedur składowanych, które zwracają wiele typów wyników, aby określić zestaw typów, które może zwracać procedura.</span><span class="sxs-lookup"><span data-stu-id="8c4fa-107">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c4fa-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c4fa-108">Example</span></span>  
 <span data-ttu-id="8c4fa-109">W poniższym przykładzie kodu SQL kształt wynik zależy od danych wejściowych (`shape =1` lub `shape = 2`).</span><span class="sxs-lookup"><span data-stu-id="8c4fa-109">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="8c4fa-110">Nie wiesz, która projekcja zostanie najpierw zwrócona.</span><span class="sxs-lookup"><span data-stu-id="8c4fa-110">You do not know which projection will be returned first.</span></span>  
  
``` sql
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="8c4fa-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c4fa-111">Example</span></span>  
 <span data-ttu-id="8c4fa-112">Aby wykonać tę procedurę składowaną, należy użyć kodu podobnego do poniższego.</span><span class="sxs-lookup"><span data-stu-id="8c4fa-112">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c4fa-113">Aby uzyskać moduł wyliczający poprawnego typu, należy użyć wzorca <xref:System.Data.Linq.IMultipleResults.GetResult%2A> na podstawie wiedzy o procedurze składowanej.</span><span class="sxs-lookup"><span data-stu-id="8c4fa-113">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="8c4fa-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c4fa-114">See also</span></span>

- [<span data-ttu-id="8c4fa-115">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="8c4fa-115">Stored Procedures</span></span>](stored-procedures.md)
