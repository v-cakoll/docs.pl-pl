---
title: System.Math, metody
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: 0b113cefa6be040924134f9d2d0cb0c9d334feef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792390"
---
# <a name="systemmath-methods"></a><span data-ttu-id="5ed71-102">System.Math, metody</span><span class="sxs-lookup"><span data-stu-id="5ed71-102">System.Math Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="5ed71-103">Program nie obsługuje następujących <xref:System.Math> metod.</span><span class="sxs-lookup"><span data-stu-id="5ed71-103">does not support the following <xref:System.Math> methods.</span></span>  
  
- <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a><span data-ttu-id="5ed71-104">Różnice od platformy .NET</span><span class="sxs-lookup"><span data-stu-id="5ed71-104">Differences from .NET</span></span>  
 <span data-ttu-id="5ed71-105">.NET Framework ma inną semantykę zaokrąglania z SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5ed71-105">The .NET Framework has different rounding semantics from SQL Server.</span></span> <span data-ttu-id="5ed71-106">Metoda w .NET Framework wykonuje *Zaokrąglenie w banku*, gdzie liczby kończące się w .5 zaokrąglają do najbliższej parzystej cyfry zamiast do kolejnej wyższej cyfry. <xref:System.Math.Round%2A></span><span class="sxs-lookup"><span data-stu-id="5ed71-106">The <xref:System.Math.Round%2A> method in the .NET Framework performs *Banker's rounding*, where numbers that ends in .5 round to the nearest even digit instead of to the next higher digit.</span></span> <span data-ttu-id="5ed71-107">Na przykład 2,5 zaokrągla do 2, a 3,5 zaokrągla do 4.</span><span class="sxs-lookup"><span data-stu-id="5ed71-107">For example, 2.5 rounds to 2, while 3.5 rounds to 4.</span></span> <span data-ttu-id="5ed71-108">(Ta technika pozwala uniknąć regularnego obciążenia w kierunku wyższych wartości w dużych transakcjach danych).</span><span class="sxs-lookup"><span data-stu-id="5ed71-108">(This technique helps avoid systematic bias toward higher values in large data transactions.)</span></span>  
  
 <span data-ttu-id="5ed71-109">W języku SQL funkcja `ROUND` zamiast tego jest zawsze zaokrąglana w kierunku od zera.</span><span class="sxs-lookup"><span data-stu-id="5ed71-109">In SQL, the `ROUND` function instead always rounds away from 0.</span></span> <span data-ttu-id="5ed71-110">W związku z tym 2,5 Zaokrąglaj do 3, kontrastowo z zaokrągleniem do 2 w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ed71-110">Therefore 2.5 rounds to 3, contrasted with its rounding to 2 in the .NET Framework.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="5ed71-111">przekazuje do semantyki SQL `ROUND` i nie próbuje zaimplementować zaokrąglenia banku.</span><span class="sxs-lookup"><span data-stu-id="5ed71-111">passes through to the SQL `ROUND` semantics and does not try to implement Banker's rounding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed71-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ed71-112">See also</span></span>

- [<span data-ttu-id="5ed71-113">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="5ed71-113">Data Types and Functions</span></span>](data-types-and-functions.md)
