---
title: 'Środki zaradcze: X509CertificateClaimSet.FindClaims Method'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e3b3645d9fc00087e163b9200edb5fbcf0dbbd9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217214"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="21510-102">Środki zaradcze: X509CertificateClaimSet.FindClaims Method</span><span class="sxs-lookup"><span data-stu-id="21510-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="21510-103">Począwszy od aplikacji, których platformą docelową [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda będzie próbował dopasować `claimType` argument w przypadku wszystkich wpisów DNS w jego polu sieci SAN.</span><span class="sxs-lookup"><span data-stu-id="21510-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)],  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="21510-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="21510-104">Impact</span></span>  
 <span data-ttu-id="21510-105">Ta zmiana dotyczy tylko aplikacji, przeznaczonych dla wersji programu .NET Framework począwszy od [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span><span class="sxs-lookup"><span data-stu-id="21510-105">This change only affects apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span></span>  
  
 <span data-ttu-id="21510-106">W przypadku aplikacji przeznaczonych dla poprzednich wersji programu .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda próbuje dopasować `claimType` argumentu tylko ostatni wpis DNS.</span><span class="sxs-lookup"><span data-stu-id="21510-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="21510-107">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="21510-107">Mitigation</span></span>  
 <span data-ttu-id="21510-108">Jeśli ta zmiana jest niepożądany, aplikacje, są przeznaczone dla wersji programu .NET Framework, począwszy od [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] można zrezygnować z go, dodając następujące ustawienie konfiguracji, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) części aplikacji plik konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="21510-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="21510-109">Ponadto aplikacje poprzedniej wersji programu .NET Framework, które są uruchomione w [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] i nowszych wersjach zgodzić się na to zachowanie, dodając następujące ustawienie konfiguracji, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)sekcję pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="21510-109">In addition, apps that target previous versions of the .NET Framework but are running under the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="21510-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21510-110">See also</span></span>

- [<span data-ttu-id="21510-111">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="21510-111">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
