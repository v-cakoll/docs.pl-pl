---
title: "Ograniczenie: Ścieżka dwukropek kontroli"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a976e4491924f91e97f01a9b98db945699655196
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="e3890-102">Ograniczenie: Ścieżka dwukropek kontroli</span><span class="sxs-lookup"><span data-stu-id="e3890-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="e3890-103">Począwszy od aplikacji przeznaczonych [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], liczba zmiany zostały wprowadzone obsługuje wcześniej nieobsługiwany ścieżek, (zarówno długość i format).</span><span class="sxs-lookup"><span data-stu-id="e3890-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="e3890-104">W szczególności sprawdzanie składni separatora właściwego dysku (dwukropek) wprowadzono więcej poprawne.</span><span class="sxs-lookup"><span data-stu-id="e3890-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e3890-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="e3890-105">Impact</span></span>  
 <span data-ttu-id="e3890-106">Te zmiany blokować niektóre ścieżki identyfikatora URI <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody wcześniej obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e3890-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e3890-107">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="e3890-107">Mitigation</span></span>  
 <span data-ttu-id="e3890-108">W celu obejścia problemu wcześniej dopuszczalne ścieżki, która nie jest już obsługiwana przez <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metod, można wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e3890-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
-   <span data-ttu-id="e3890-109">Ręcznie usuń system z adresu URL.</span><span class="sxs-lookup"><span data-stu-id="e3890-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="e3890-110">Na przykład usunąć `file://` z adresu URL.</span><span class="sxs-lookup"><span data-stu-id="e3890-110">For example, remove `file://` from a URL.</span></span>  
  
-   <span data-ttu-id="e3890-111">Identyfikator URI do przekazania <xref:System.Uri> konstruktora i pobrać wartość <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e3890-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
-   <span data-ttu-id="e3890-112">Zrezygnować z nowego normalizacji ścieżka przez ustawienie `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> przełączyć się do `true`.</span><span class="sxs-lookup"><span data-stu-id="e3890-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e3890-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3890-113">See Also</span></span>  
 [<span data-ttu-id="e3890-114">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="e3890-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
