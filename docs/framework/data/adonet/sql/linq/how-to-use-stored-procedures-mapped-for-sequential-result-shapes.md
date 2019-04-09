---
title: 'Instrukcje: Używanie procedur składowanych zamapowanych na sekwencyjne kształty wyników'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: e51ebacb3f6be849f7b871f2d12db3ea7476b117
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134514"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="0bec2-102">Instrukcje: Używanie procedur składowanych zamapowanych na sekwencyjne kształty wyników</span><span class="sxs-lookup"><span data-stu-id="0bec2-102">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>
<span data-ttu-id="0bec2-103">Ten rodzaj procedury składowanej można wygenerować więcej niż jeden kształt wyniku, ale wiesz, w jakiej kolejności wyniki są zwracane.</span><span class="sxs-lookup"><span data-stu-id="0bec2-103">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="0bec2-104">Natomiast tego scenariusza ze scenariuszem, których nie znasz sekwencji zwraca.</span><span class="sxs-lookup"><span data-stu-id="0bec2-104">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="0bec2-105">Aby uzyskać więcej informacji, zobacz [jak: Używanie procedur składowanych zmapowanych do wielu kształtów wyników](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="0bec2-105">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bec2-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="0bec2-106">Example</span></span>  
 <span data-ttu-id="0bec2-107">Oto języka T-SQL procedury przechowywanej, która zwraca sekwencyjnie wielu kształtów wyników:</span><span class="sxs-lookup"><span data-stu-id="0bec2-107">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="0bec2-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0bec2-108">Example</span></span>  
 <span data-ttu-id="0bec2-109">Aby wykonać tę procedurę składowaną należy użyć kodu podobnego do następującego.</span><span class="sxs-lookup"><span data-stu-id="0bec2-109">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="0bec2-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0bec2-110">See also</span></span>

- [<span data-ttu-id="0bec2-111">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="0bec2-111">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
