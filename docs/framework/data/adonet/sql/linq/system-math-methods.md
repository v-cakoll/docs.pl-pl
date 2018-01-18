---
title: Metody System.Math
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cfcbf915703c72211fc9d958abfda7ffac8aafdc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="systemmath-methods"></a><span data-ttu-id="9fdc5-102">Metody System.Math</span><span class="sxs-lookup"><span data-stu-id="9fdc5-102">System.Math Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9fdc5-103">nie obsługuje następujących <xref:System.Math> metody.</span><span class="sxs-lookup"><span data-stu-id="9fdc5-103"> does not support the following <xref:System.Math> methods.</span></span>  
  
-   <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a><span data-ttu-id="9fdc5-104">Różnice z platformy .NET</span><span class="sxs-lookup"><span data-stu-id="9fdc5-104">Differences from .NET</span></span>  
 <span data-ttu-id="9fdc5-105">.NET Framework ma semantykę różną zaokrąglania z programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9fdc5-105">The .NET Framework has different rounding semantics from SQL Server.</span></span> <span data-ttu-id="9fdc5-106"><xref:System.Math.Round%2A> Wykonuje metodę w programie .NET Framework *zaokrąglenie do zaokrąglania*, gdzie numery, które kończy się.5 zaokrąglona do najbliższej nawet cyfr zamiast z następnym wyższym cyfry.</span><span class="sxs-lookup"><span data-stu-id="9fdc5-106">The <xref:System.Math.Round%2A> method in the .NET Framework performs *Banker's rounding*, where numbers that ends in .5 round to the nearest even digit instead of to the next higher digit.</span></span> <span data-ttu-id="9fdc5-107">Na przykład 2.5 powoduje zaokrąglenie do 2, podczas gdy 3.5 powoduje zaokrąglenie do 4.</span><span class="sxs-lookup"><span data-stu-id="9fdc5-107">For example, 2.5 rounds to 2, while 3.5 rounds to 4.</span></span> <span data-ttu-id="9fdc5-108">(Ta technika pomaga uniknąć systematyczne odchylenia kierunku wyższe wartości w transakcji dużej ilości danych).</span><span class="sxs-lookup"><span data-stu-id="9fdc5-108">(This technique helps avoid systematic bias toward higher values in large data transactions.)</span></span>  
  
 <span data-ttu-id="9fdc5-109">W programie SQL `ROUND` funkcja zamiast zawsze zaokrągla wartość w kierunku od 0.</span><span class="sxs-lookup"><span data-stu-id="9fdc5-109">In SQL, the `ROUND` function instead always rounds away from 0.</span></span> <span data-ttu-id="9fdc5-110">W związku z tym 2.5 powoduje zaokrąglenie do 3 odróżniające z zaokrąglania 2 w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9fdc5-110">Therefore 2.5 rounds to 3, contrasted with its rounding to 2 in the .NET Framework.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9fdc5-111">Przechodzi do SQL `ROUND` semantykę i nie próbuje zaimplementować zaokrąglenie kwot.</span><span class="sxs-lookup"><span data-stu-id="9fdc5-111"> passes through to the SQL `ROUND` semantics and does not try to implement Banker's rounding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fdc5-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fdc5-112">See Also</span></span>  
 [<span data-ttu-id="9fdc5-113">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="9fdc5-113">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
