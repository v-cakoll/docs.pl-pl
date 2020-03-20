---
title: 'Łagodzenie: Kontrola dwukropek ścieżki'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: c6e1106b6f5d8457417992941b9f28712d484442
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181244"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="49777-102">Łagodzenie: Kontrola dwukropek ścieżki</span><span class="sxs-lookup"><span data-stu-id="49777-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="49777-103">Począwszy od aplikacji, które są przeznaczone dla programu .NET Framework 4.6.2, wprowadzono szereg zmian w celu obsługi wcześniej nieobsługiwał ścieżek (zarówno pod względem długości i formatu).</span><span class="sxs-lookup"><span data-stu-id="49777-103">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="49777-104">W szczególności, kontrole prawidłowej składni separatora dysku (dwukropek) zostały bardziej poprawne.</span><span class="sxs-lookup"><span data-stu-id="49777-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="49777-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="49777-105">Impact</span></span>  
 <span data-ttu-id="49777-106">Te zmiany blokują niektóre <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ścieżki <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> URI i metody wcześniej obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="49777-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="49777-107">Środki zaradcze</span><span class="sxs-lookup"><span data-stu-id="49777-107">Mitigation</span></span>  
 <span data-ttu-id="49777-108">Aby obejść problem wcześniej akceptowalnej ścieżki, która nie <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> jest <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> już obsługiwana przez metody i, można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="49777-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="49777-109">Ręcznie usuń schemat z adresu URL.</span><span class="sxs-lookup"><span data-stu-id="49777-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="49777-110">Na przykład `file://` usuń z adresu URL.</span><span class="sxs-lookup"><span data-stu-id="49777-110">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="49777-111">Przekaż identyfikator URI <xref:System.Uri> do konstruktora i <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> pobrać wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="49777-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="49777-112">Zrezygnuj z normalizacji `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> nowej `true`ścieżki, ustawiając przełącznik na .</span><span class="sxs-lookup"><span data-stu-id="49777-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="49777-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49777-113">See also</span></span>

- [<span data-ttu-id="49777-114">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="49777-114">Application compatibility</span></span>](application-compatibility.md)
