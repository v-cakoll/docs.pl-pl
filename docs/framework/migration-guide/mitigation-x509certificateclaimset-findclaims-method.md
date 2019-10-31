---
title: 'Ograniczanie: X509CertificateClaimSet. FindClaims Metoda'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: 5591ecebeb924f84cc0efdaf78f40f9d835d2d02
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126084"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="06282-102">Ograniczanie: X509CertificateClaimSet. FindClaims Metoda</span><span class="sxs-lookup"><span data-stu-id="06282-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="06282-103">Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6.1, Metoda <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> podejmie próbę dopasowania argumentu `claimType` ze wszystkimi wpisami DNS w jego polu SAN.</span><span class="sxs-lookup"><span data-stu-id="06282-103">Starting with apps that target the .NET Framework 4.6.1,  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="06282-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="06282-104">Impact</span></span>  
 <span data-ttu-id="06282-105">Ta zmiana ma wpływ tylko na aplikacje, które są przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="06282-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="06282-106">W przypadku aplikacji przeznaczonych dla poprzednich wersji .NET Framework Metoda <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> próbuje dopasować argument `claimType` tylko do ostatniego wpisu DNS.</span><span class="sxs-lookup"><span data-stu-id="06282-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="06282-107">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="06282-107">Mitigation</span></span>  
 <span data-ttu-id="06282-108">Jeśli ta zmiana jest niepożądana, aplikacje, które są przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1 mogą zrezygnować z niego, dodając następujące ustawienia konfiguracji [\<do sekcji > Runtime](../configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracyjnym aplikacji:</span><span class="sxs-lookup"><span data-stu-id="06282-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="06282-109">Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework, ale działają w ramach .NET Framework 4.6.1 i nowszych wersji, mogą zrezygnować z tego zachowania, dodając następujące ustawienia konfiguracji do sekcji [> środowiska uruchomieniowego\<](../configure-apps/file-schema/runtime/runtime-element.md) plik konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="06282-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="06282-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06282-110">See also</span></span>

- [<span data-ttu-id="06282-111">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="06282-111">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
