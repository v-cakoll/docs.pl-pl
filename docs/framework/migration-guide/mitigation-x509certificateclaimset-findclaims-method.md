---
title: Środki zaradcze X509CertificateClaimSet.FindClaims Method
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffc03e6c88a2aabb967587d8b1ee7d0b784b4e7d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70778933"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="b8c6e-102">Środki zaradcze X509CertificateClaimSet.FindClaims Method</span><span class="sxs-lookup"><span data-stu-id="b8c6e-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="b8c6e-103">Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6.1 <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> , Metoda podejmie próbę `claimType` dopasowania argumentu ze wszystkimi wpisami DNS w jego polu sieci SAN.</span><span class="sxs-lookup"><span data-stu-id="b8c6e-103">Starting with apps that target the .NET Framework 4.6.1,  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="b8c6e-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="b8c6e-104">Impact</span></span>  
 <span data-ttu-id="b8c6e-105">Ta zmiana ma wpływ tylko na aplikacje, które są przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="b8c6e-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="b8c6e-106">W przypadku aplikacji przeznaczonych dla poprzednich wersji .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> Metoda próbuje `claimType` dopasować argument tylko do ostatniego wpisu DNS.</span><span class="sxs-lookup"><span data-stu-id="b8c6e-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="b8c6e-107">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="b8c6e-107">Mitigation</span></span>  
 <span data-ttu-id="b8c6e-108">Jeśli ta zmiana jest niepożądana, aplikacje przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1 mogą zrezygnować z niego, dodając następujące ustawienia konfiguracji do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracji aplikacji :</span><span class="sxs-lookup"><span data-stu-id="b8c6e-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="b8c6e-109">Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework ale działają w ramach .NET Framework 4.6.1 i nowszych wersji, mogą zrezygnować z tego zachowania, dodając następujące ustawienia konfiguracji do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) plik konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="b8c6e-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8c6e-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8c6e-110">See also</span></span>

- [<span data-ttu-id="b8c6e-111">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="b8c6e-111">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
