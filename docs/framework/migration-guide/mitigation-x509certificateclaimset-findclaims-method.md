---
title: "Środki zaradcze: Metoda X509CertificateClaimSet.FindClaims"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f7872f1904cfcab860bb25459aabd47e6dcf38ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="0e002-102">Środki zaradcze: Metoda X509CertificateClaimSet.FindClaims</span><span class="sxs-lookup"><span data-stu-id="0e002-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="0e002-103">Począwszy od aplikacji przeznaczonych [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda będzie próbował dopasować `claimType` argumentu z wszystkie wpisy DNS w polu sieci SAN.</span><span class="sxs-lookup"><span data-stu-id="0e002-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)],  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="0e002-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="0e002-104">Impact</span></span>  
 <span data-ttu-id="0e002-105">Ta zmiana wpływa tylko na aplikacje, które odnoszą się do wersji programu .NET Framework począwszy [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0e002-105">This change only affects apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span></span>  
  
 <span data-ttu-id="0e002-106">W przypadku aplikacji, które odnoszą się do poprzednich wersji programu .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda próbuje dopasować `claimType` argument tylko z ostatni wpis DNS.</span><span class="sxs-lookup"><span data-stu-id="0e002-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="0e002-107">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="0e002-107">Mitigation</span></span>  
 <span data-ttu-id="0e002-108">Jeśli ta zmiana jest niepożądane, aplikacje których docelowe wersje programu .NET Framework, począwszy od [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] można zrezygnować z go, dodając następujące ustawienia konfiguracji do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) części aplikacji plik konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="0e002-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="0e002-109">Ponadto aplikacje docelowe poprzednie wersje programu .NET Framework, które działają w ramach [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] i nowszych wersjach zgodzić się na ten problem, dodając następujące ustawienia konfiguracji do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)sekcji pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="0e002-109">In addition, apps that target previous versions of the .NET Framework but are running under the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e002-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e002-110">See Also</span></span>  
 [<span data-ttu-id="0e002-111">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="0e002-111">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
