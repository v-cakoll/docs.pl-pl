---
title: 'Łagodzenie: X509CertificateClaimSet.FindClaims Metoda'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: 0b306960c4f11bb6f54aecaeb13297e7725e16a8
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102648"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="20577-102">Łagodzenie: X509CertificateClaimSet.FindClaims Metoda</span><span class="sxs-lookup"><span data-stu-id="20577-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>

<span data-ttu-id="20577-103">Począwszy od aplikacji docelowych .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> 4.6.1, `claimType` metoda będzie próbować dopasować argument do wszystkich wpisów DNS w polu SAN.</span><span class="sxs-lookup"><span data-stu-id="20577-103">Starting with apps that target .NET Framework 4.6.1, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="20577-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="20577-104">Impact</span></span>  
 <span data-ttu-id="20577-105">Ta zmiana dotyczy tylko aplikacji, które docelowe wersje programu .NET Framework, począwszy od programu .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="20577-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="20577-106">W przypadku aplikacji przeznaczonych dla poprzednich <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> wersji programu .NET Framework metoda próbuje dopasować `claimType` argument tylko do ostatniego wpisu DNS.</span><span class="sxs-lookup"><span data-stu-id="20577-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="20577-107">Środki zaradcze</span><span class="sxs-lookup"><span data-stu-id="20577-107">Mitigation</span></span>  
 <span data-ttu-id="20577-108">Jeśli ta zmiana jest niepożądana, aplikacje docelowe wersji programu .NET Framework, począwszy od programu .NET Framework 4.6.1, mogą zrezygnować z niej, dodając następujące ustawienie konfiguracji do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracyjnego aplikacji:</span><span class="sxs-lookup"><span data-stu-id="20577-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 <span data-ttu-id="20577-109">Ponadto aplikacje przeznaczone dla poprzednich wersji programu .NET Framework, ale uruchomione w ramach programu .NET Framework 4.6.1 i nowszych wersji mogą zdecydować się na to zachowanie, dodając następujące ustawienie konfiguracji do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracyjnego aplikacji:</span><span class="sxs-lookup"><span data-stu-id="20577-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="20577-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20577-110">See also</span></span>

- [<span data-ttu-id="20577-111">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="20577-111">Application compatibility</span></span>](application-compatibility.md)
