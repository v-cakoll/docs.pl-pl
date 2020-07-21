---
title: 'Ograniczanie: X509CertificateClaimSet. FindClaims Metoda'
description: Dowiedz się, jak zmieniono metodę X509CertificateClaimSet. FindClaims dla aplikacji, które są przeznaczone .NET Framework 4.6.1.
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: 304d8fb5adc27b33f2410faaaf8662e0ff9be66d
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475323"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="683e2-103">Ograniczanie: X509CertificateClaimSet. FindClaims Metoda</span><span class="sxs-lookup"><span data-stu-id="683e2-103">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>

<span data-ttu-id="683e2-104">Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6.1, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> Metoda podejmie próbę dopasowania `claimType` argumentu ze wszystkimi wpisami DNS w jego polu sieci SAN.</span><span class="sxs-lookup"><span data-stu-id="683e2-104">Starting with apps that target .NET Framework 4.6.1, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="683e2-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="683e2-105">Impact</span></span>  
 <span data-ttu-id="683e2-106">Ta zmiana ma wpływ tylko na aplikacje, które są przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="683e2-106">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="683e2-107">W przypadku aplikacji przeznaczonych dla poprzednich wersji .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> Metoda próbuje dopasować `claimType` argument tylko do ostatniego wpisu DNS.</span><span class="sxs-lookup"><span data-stu-id="683e2-107">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="683e2-108">Ograniczanie ryzyka</span><span class="sxs-lookup"><span data-stu-id="683e2-108">Mitigation</span></span>  
 <span data-ttu-id="683e2-109">Jeśli ta zmiana jest niepożądana, aplikacje przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1 mogą zrezygnować z niego, dodając następujące ustawienia konfiguracji do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="683e2-109">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 <span data-ttu-id="683e2-110">Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework ale działają w ramach .NET Framework 4.6.1 i nowszych wersji, mogą zrezygnować z tego zachowania, dodając następujące ustawienia konfiguracji do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="683e2-110">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="683e2-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="683e2-111">See also</span></span>

- [<span data-ttu-id="683e2-112">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="683e2-112">Application compatibility</span></span>](application-compatibility.md)
