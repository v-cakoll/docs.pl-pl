---
title: System.Math, metody
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: 1dae31b30962505c07c198f3bd35fceb8f400efb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917686"
---
# <a name="systemmath-methods"></a><span data-ttu-id="e45b7-102">System.Math, metody</span><span class="sxs-lookup"><span data-stu-id="e45b7-102">System.Math Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e45b7-103">nie obsługuje następujących <xref:System.Math> metody.</span><span class="sxs-lookup"><span data-stu-id="e45b7-103">does not support the following <xref:System.Math> methods.</span></span>  
  
- <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a><span data-ttu-id="e45b7-104">Różnice z platformy .NET</span><span class="sxs-lookup"><span data-stu-id="e45b7-104">Differences from .NET</span></span>  
 <span data-ttu-id="e45b7-105">.NET Framework ma semantykę różną zaokrąglania, z programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e45b7-105">The .NET Framework has different rounding semantics from SQL Server.</span></span> <span data-ttu-id="e45b7-106"><xref:System.Math.Round%2A> Wykonuje metodę w programie .NET Framework *Banker przez zaokrąglenie*, gdzie liczb, które kończy się.5 zaokrąglona do najbliższej cyfry nawet zamiast kolejną cyfrą wyższy.</span><span class="sxs-lookup"><span data-stu-id="e45b7-106">The <xref:System.Math.Round%2A> method in the .NET Framework performs *Banker's rounding*, where numbers that ends in .5 round to the nearest even digit instead of to the next higher digit.</span></span> <span data-ttu-id="e45b7-107">Na przykład 2.5 Zaokrągla 2, podczas gdy 3.5 powoduje zaokrąglenie do 4.</span><span class="sxs-lookup"><span data-stu-id="e45b7-107">For example, 2.5 rounds to 2, while 3.5 rounds to 4.</span></span> <span data-ttu-id="e45b7-108">(Ta technika pomaga uniknąć systematyczne odchylenie kierunku wyższe wartości w transakcjach dużych ilości danych).</span><span class="sxs-lookup"><span data-stu-id="e45b7-108">(This technique helps avoid systematic bias toward higher values in large data transactions.)</span></span>  
  
 <span data-ttu-id="e45b7-109">W programie SQL `ROUND` zamiast zawsze zaokrągla liczbę od 0.</span><span class="sxs-lookup"><span data-stu-id="e45b7-109">In SQL, the `ROUND` function instead always rounds away from 0.</span></span> <span data-ttu-id="e45b7-110">W związku z tym 2.5 zaokrągla do 3, porównanie z zaokrąglaniem do 2 w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e45b7-110">Therefore 2.5 rounds to 3, contrasted with its rounding to 2 in the .NET Framework.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e45b7-111">Przechodzi do bazy danych SQL `ROUND` semantyki i nie podejmuje próby wykonania zaokrąglenie kwot.</span><span class="sxs-lookup"><span data-stu-id="e45b7-111">passes through to the SQL `ROUND` semantics and does not try to implement Banker's rounding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e45b7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e45b7-112">See also</span></span>

- [<span data-ttu-id="e45b7-113">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="e45b7-113">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
