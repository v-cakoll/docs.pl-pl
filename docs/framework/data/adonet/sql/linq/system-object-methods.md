---
title: Metody System.Object
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6998c2b00a2b8e83bc79ae7ba1dd01ea549cf5df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="systemobject-methods"></a><span data-ttu-id="6790a-102">Metody System.Object</span><span class="sxs-lookup"><span data-stu-id="6790a-102">System.Object Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6790a-103">obsługuje następujące <xref:System.Object> metody.</span><span class="sxs-lookup"><span data-stu-id="6790a-103"> supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6790a-104">nie obsługuje następujących <xref:System.Object> metody.</span><span class="sxs-lookup"><span data-stu-id="6790a-104"> does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="6790a-105"><xref:System.Object.ToString?displayProperty=nameWithType>dla pliku binarnego takich jak typy `BINARY`, `VARBINARY`, `IMAGE`, i `TIMESTAMP`.</span><span class="sxs-lookup"><span data-stu-id="6790a-105"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="6790a-106">Różnice z platformy .NET</span><span class="sxs-lookup"><span data-stu-id="6790a-106">Differences from .NET</span></span>  
 <span data-ttu-id="6790a-107">Dane wyjściowe <xref:System.Object.ToString?displayProperty=nameWithType> dla typu double używa SQL `CONVERT`(NVARCHAR(30), @x, 2) na SQL.</span><span class="sxs-lookup"><span data-stu-id="6790a-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="6790a-108">SQL zawsze używa 16 cyfr i notacja naukowa w tym przypadku (na przykład "0.000000000000000e + 000" 0).</span><span class="sxs-lookup"><span data-stu-id="6790a-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="6790a-109">W związku z tym <xref:System.Object.ToString?displayProperty=nameWithType> konwersji nie tworzy tych samych parametrach jako <xref:System.Convert.ToString%2A?displayProperty=nameWithType> w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6790a-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6790a-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6790a-110">See Also</span></span>  
 [<span data-ttu-id="6790a-111">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="6790a-111">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
