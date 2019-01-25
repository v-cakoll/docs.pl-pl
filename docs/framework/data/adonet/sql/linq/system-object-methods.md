---
title: Metody System.Object
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: cae06286b77e23718facfc5be2b0ac2d27381ad3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713421"
---
# <a name="systemobject-methods"></a><span data-ttu-id="3d7a0-102">Metody System.Object</span><span class="sxs-lookup"><span data-stu-id="3d7a0-102">System.Object Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="3d7a0-103">obsługuje następujące <xref:System.Object> metody.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-103">supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="3d7a0-104">nie obsługuje następujących <xref:System.Object> metody.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-104">does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="3d7a0-105"><xref:System.Object.ToString?displayProperty=nameWithType> dla pliku binarnego typy takie jak `BINARY`, `VARBINARY`, `IMAGE`, i `TIMESTAMP`.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-105"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="3d7a0-106">Różnice z platformy .NET</span><span class="sxs-lookup"><span data-stu-id="3d7a0-106">Differences from .NET</span></span>  
 <span data-ttu-id="3d7a0-107">Dane wyjściowe <xref:System.Object.ToString?displayProperty=nameWithType> dla podwójnej precyzji SQL `CONVERT`(NVARCHAR(30), @x, 2) w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="3d7a0-108">SQL zawsze używa 16 cyfr i notacji wykładniczej w tym przypadku (na przykład "0.000000000000000e + 000" 0).</span><span class="sxs-lookup"><span data-stu-id="3d7a0-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="3d7a0-109">W rezultacie <xref:System.Object.ToString?displayProperty=nameWithType> konwersji nie daje ten sam ciąg jako <xref:System.Convert.ToString%2A?displayProperty=nameWithType> w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d7a0-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d7a0-110">See also</span></span>
- [<span data-ttu-id="3d7a0-111">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="3d7a0-111">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
