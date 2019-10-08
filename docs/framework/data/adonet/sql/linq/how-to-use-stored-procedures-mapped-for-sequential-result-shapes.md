---
title: 'Instrukcje: używanie procedur składowanych mapowanych dla sekwencyjnych kształtów wyników'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 8378a175ab2479ab9769ca08579e1c89269eaba4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003223"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="18886-102">Instrukcje: używanie procedur składowanych mapowanych dla sekwencyjnych kształtów wyników</span><span class="sxs-lookup"><span data-stu-id="18886-102">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>
<span data-ttu-id="18886-103">Ten rodzaj procedury składowanej może generować więcej niż jeden kształt wynikowy, ale wiadomo, w jakiej kolejności zwracane są wyniki.</span><span class="sxs-lookup"><span data-stu-id="18886-103">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="18886-104">Ten scenariusz należy wykonać w scenariuszu, w którym nie jest znana sekwencja zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="18886-104">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="18886-105">Aby uzyskać więcej informacji, zobacz [How to: use procedur składowanych mapowanych na wiele kształtów wynikowych](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="18886-105">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18886-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="18886-106">Example</span></span>  
 <span data-ttu-id="18886-107">Poniżej znajduje się T-SQL procedury składowanej zwracającej wiele kształtów wyników sekwencyjnie:</span><span class="sxs-lookup"><span data-stu-id="18886-107">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```sql
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="18886-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="18886-108">Example</span></span>  
 <span data-ttu-id="18886-109">Aby wykonać tę procedurę składowaną, należy użyć kodu podobnego do poniższego.</span><span class="sxs-lookup"><span data-stu-id="18886-109">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="18886-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18886-110">See also</span></span>

- [<span data-ttu-id="18886-111">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="18886-111">Stored Procedures</span></span>](stored-procedures.md)
