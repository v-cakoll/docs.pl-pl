---
title: "Porady: Użyj procedur składowanych mapowane do wyniku sekwencyjnych kształtów"
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
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 227fe2c777d23172caba5f290d9626552af4747a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="ed986-102">Porady: Użyj procedur składowanych mapowane do wyniku sekwencyjnych kształtów</span><span class="sxs-lookup"><span data-stu-id="ed986-102">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>
<span data-ttu-id="ed986-103">Ten rodzaj procedury składowanej można wygenerować więcej niż jeden kształt wyniku, ale wiesz, w jakiej kolejności są zwracane.</span><span class="sxs-lookup"><span data-stu-id="ed986-103">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="ed986-104">Natomiast ten scenariusz ze scenariuszem, jeżeli nie znasz sekwencji danych.</span><span class="sxs-lookup"><span data-stu-id="ed986-104">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="ed986-105">Aby uzyskać więcej informacji, zobacz [porady: użycie przechowywanych procedur mapowane do wielu kształtów wynik](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="ed986-105">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed986-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ed986-106">Example</span></span>  
 <span data-ttu-id="ed986-107">Oto T-SQL procedury przechowywanej, która zwraca sekwencyjnie wielu kształtów wyników:</span><span class="sxs-lookup"><span data-stu-id="ed986-107">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="ed986-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="ed986-108">Example</span></span>  
 <span data-ttu-id="ed986-109">Należy użyć podobny do następującego kodu, aby wykonać tę procedurę składowaną.</span><span class="sxs-lookup"><span data-stu-id="ed986-109">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="ed986-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed986-110">See Also</span></span>  
 [<span data-ttu-id="ed986-111">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="ed986-111">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
