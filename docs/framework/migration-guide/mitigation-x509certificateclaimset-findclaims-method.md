---
title: 'Środki zaradcze: X509CertificateClaimSet.FindClaims Method'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7fb1eb0c502584caac11ca3dde6e7e646b29cfe
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251092"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="3c871-102">Środki zaradcze: X509CertificateClaimSet.FindClaims Method</span><span class="sxs-lookup"><span data-stu-id="3c871-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="3c871-103">Począwszy od aplikacji przeznaczonych dla platformy .NET Framework 4.6.1, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda będzie próbował dopasować `claimType` argument w przypadku wszystkich wpisów DNS w jego polu sieci SAN.</span><span class="sxs-lookup"><span data-stu-id="3c871-103">Starting with apps that target the .NET Framework 4.6.1,  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="3c871-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="3c871-104">Impact</span></span>  
 <span data-ttu-id="3c871-105">Ta zmiana dotyczy tylko aplikacji, przeznaczonych dla wersji programu .NET Framework, począwszy od programu .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="3c871-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="3c871-106">W przypadku aplikacji przeznaczonych dla poprzednich wersji programu .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda próbuje dopasować `claimType` argumentu tylko ostatni wpis DNS.</span><span class="sxs-lookup"><span data-stu-id="3c871-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="3c871-107">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="3c871-107">Mitigation</span></span>  
 <span data-ttu-id="3c871-108">Jeśli ta zmiana jest niepożądany, aplikacji przeznaczonych dla wersji programu .NET Framework, począwszy od programu .NET Framework 4.6.1 można zrezygnować z go, dodając następujące ustawienie konfiguracji, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji plik konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="3c871-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="3c871-109">Ponadto aplikacje poprzedniej wersji programu .NET Framework, które są uruchomione w .NET Framework 4.6.1 i nowszych wersjach zgodzić się na to zachowanie, dodając następujące ustawienie konfiguracji, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcję pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="3c871-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c871-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c871-110">See also</span></span>

- [<span data-ttu-id="3c871-111">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="3c871-111">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
