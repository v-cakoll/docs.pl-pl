---
title: 'Środki zaradcze: Ścieżka dwukropek kontroli'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 342c3ce59ad80c9a60f2a2b69b30f77ff0549415
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176764"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="08ea6-102">Środki zaradcze: Ścieżka dwukropek kontroli</span><span class="sxs-lookup"><span data-stu-id="08ea6-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="08ea6-103">Począwszy od aplikacji, których platformą docelową [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], wprowadzono szereg zmian obsługuje wcześniej nieobsługiwanych ścieżek, (zarówno pod względem długość i formatu).</span><span class="sxs-lookup"><span data-stu-id="08ea6-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="08ea6-104">W szczególności sprawdza, czy składnia separator odpowiedniego dysku (dwukropek) wprowadzono bardziej poprawny.</span><span class="sxs-lookup"><span data-stu-id="08ea6-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="08ea6-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="08ea6-105">Impact</span></span>  
 <span data-ttu-id="08ea6-106">Te zmiany blokować niektóre ścieżki identyfikatora URI <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody wcześniej obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="08ea6-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="08ea6-107">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="08ea6-107">Mitigation</span></span>  
 <span data-ttu-id="08ea6-108">Aby obejść ten problem wcześniej akceptowalną ścieżką, która nie jest już obsługiwany przez <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metod, wykonasz następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="08ea6-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
-   <span data-ttu-id="08ea6-109">Ręcznie usuń schemat z adresu URL.</span><span class="sxs-lookup"><span data-stu-id="08ea6-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="08ea6-110">Na przykład usunąć `file://` z adresu URL.</span><span class="sxs-lookup"><span data-stu-id="08ea6-110">For example, remove `file://` from a URL.</span></span>  
  
-   <span data-ttu-id="08ea6-111">Przekaż identyfikator URI do <xref:System.Uri> konstruktora i pobrać wartość <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="08ea6-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
-   <span data-ttu-id="08ea6-112">Zrezygnować z nowych normalizacji ścieżki, ustawiając `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> przełączyć się do `true`.</span><span class="sxs-lookup"><span data-stu-id="08ea6-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="08ea6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08ea6-113">See also</span></span>

- [<span data-ttu-id="08ea6-114">Zmiany przekierowania</span><span class="sxs-lookup"><span data-stu-id="08ea6-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
