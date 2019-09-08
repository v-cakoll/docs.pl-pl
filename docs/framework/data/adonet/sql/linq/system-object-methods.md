---
title: System.Object, metody
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: d1a36798ef789bbc44f581dfc631feee19e1f66b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781074"
---
# <a name="systemobject-methods"></a><span data-ttu-id="7ee9c-102">System.Object, metody</span><span class="sxs-lookup"><span data-stu-id="7ee9c-102">System.Object Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7ee9c-103">obsługuje następujące <xref:System.Object> metody.</span><span class="sxs-lookup"><span data-stu-id="7ee9c-103">supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7ee9c-104">Program nie obsługuje następujących <xref:System.Object> metod.</span><span class="sxs-lookup"><span data-stu-id="7ee9c-104">does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="7ee9c-105"><xref:System.Object.ToString?displayProperty=nameWithType>w przypadku typów binarnych `BINARY`, `VARBINARY`takich `IMAGE`jak, `TIMESTAMP`, i.</span><span class="sxs-lookup"><span data-stu-id="7ee9c-105"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="7ee9c-106">Różnice od platformy .NET</span><span class="sxs-lookup"><span data-stu-id="7ee9c-106">Differences from .NET</span></span>  
 <span data-ttu-id="7ee9c-107">Dane wyjściowe <xref:System.Object.ToString?displayProperty=nameWithType> dla elementu Double używają języka `CONVERT`SQL (nvarchar (30) @x,, 2) na serwerze SQL.</span><span class="sxs-lookup"><span data-stu-id="7ee9c-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="7ee9c-108">W tym przypadku SQL zawsze używa 16 cyfr i notacji wykładniczej (na przykład "0.000000000000000 e + 000" dla 0).</span><span class="sxs-lookup"><span data-stu-id="7ee9c-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="7ee9c-109">W związku <xref:System.Object.ToString?displayProperty=nameWithType> z tym konwersja nie produkuje tego samego ciągu co <xref:System.Convert.ToString%2A?displayProperty=nameWithType> w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7ee9c-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee9c-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ee9c-110">See also</span></span>

- [<span data-ttu-id="7ee9c-111">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="7ee9c-111">Data Types and Functions</span></span>](data-types-and-functions.md)
