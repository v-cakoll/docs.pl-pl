---
title: 'Środki zaradcze: sprawdzanie dwukropka ścieżki'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: e88643fea3bd507289436f41880a2de34117884f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457898"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="ad126-102">Środki zaradcze: sprawdzanie dwukropka ścieżki</span><span class="sxs-lookup"><span data-stu-id="ad126-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="ad126-103">Począwszy od aplikacji odnoszących się do .NET Framework 4.6.2, wprowadzono wiele zmian do obsługi poprzednio nieobsługiwanych ścieżek (zarówno pod względem długości, jak i formatu).</span><span class="sxs-lookup"><span data-stu-id="ad126-103">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="ad126-104">W szczególności sprawdza poprawność składni separatora dysku (dwukropek).</span><span class="sxs-lookup"><span data-stu-id="ad126-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="ad126-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="ad126-105">Impact</span></span>  
 <span data-ttu-id="ad126-106">Te zmiany blokują niektóre ścieżki URI <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody, które wcześniej były obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ad126-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="ad126-107">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="ad126-107">Mitigation</span></span>  
 <span data-ttu-id="ad126-108">Aby obejść problem z wcześniej akceptowalną ścieżką, która nie jest już obsługiwana przez <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody, można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ad126-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="ad126-109">Ręcznie usuń schemat z adresu URL.</span><span class="sxs-lookup"><span data-stu-id="ad126-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="ad126-110">Na przykład Usuń `file://` z adresu URL.</span><span class="sxs-lookup"><span data-stu-id="ad126-110">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="ad126-111">Przekaż identyfikator URI do konstruktora <xref:System.Uri> i Pobierz wartość właściwości <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ad126-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="ad126-112">Zrezygnuj z nowej normalizacji ścieżki, ustawiając przełącznik `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> do `true`.</span><span class="sxs-lookup"><span data-stu-id="ad126-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ad126-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad126-113">See also</span></span>

- [<span data-ttu-id="ad126-114">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="ad126-114">Application compatibility</span></span>](application-compatibility.md)
