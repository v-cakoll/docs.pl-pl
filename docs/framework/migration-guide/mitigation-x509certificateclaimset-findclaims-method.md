---
title: 'Ograniczanie: X509CertificateClaimSet. FindClaims Metoda'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: e75b1cae599b153012b8525a0e1e36ed116e695f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457755"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="fcf84-102">Ograniczanie: X509CertificateClaimSet. FindClaims Metoda</span><span class="sxs-lookup"><span data-stu-id="fcf84-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="fcf84-103">Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6.1, Metoda <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> podejmie próbę dopasowania argumentu `claimType` ze wszystkimi wpisami DNS w jego polu SAN.</span><span class="sxs-lookup"><span data-stu-id="fcf84-103">Starting with apps that target the .NET Framework 4.6.1,  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="fcf84-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="fcf84-104">Impact</span></span>  
 <span data-ttu-id="fcf84-105">Ta zmiana ma wpływ tylko na aplikacje, które są przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="fcf84-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="fcf84-106">W przypadku aplikacji przeznaczonych dla poprzednich wersji .NET Framework Metoda <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> próbuje dopasować argument `claimType` tylko do ostatniego wpisu DNS.</span><span class="sxs-lookup"><span data-stu-id="fcf84-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="fcf84-107">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="fcf84-107">Mitigation</span></span>  
 <span data-ttu-id="fcf84-108">Jeśli ta zmiana jest niepożądana, aplikacje, które są przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1 mogą zrezygnować z niego, dodając następujące ustawienia konfiguracji [\<do sekcji > Runtime](../configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracyjnym aplikacji:</span><span class="sxs-lookup"><span data-stu-id="fcf84-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="fcf84-109">Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework, ale działają w ramach .NET Framework 4.6.1 i nowszych wersji, mogą zrezygnować z tego zachowania, dodając następujące ustawienia konfiguracji do sekcji [> środowiska uruchomieniowego\<](../configure-apps/file-schema/runtime/runtime-element.md) plik konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="fcf84-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fcf84-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fcf84-110">See also</span></span>

- [<span data-ttu-id="fcf84-111">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="fcf84-111">Application compatibility</span></span>](application-compatibility.md)
