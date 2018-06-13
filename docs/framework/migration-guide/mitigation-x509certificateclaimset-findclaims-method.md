---
title: 'Środki zaradcze: Metoda X509CertificateClaimSet.FindClaims'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b927ed2e68ddea537f87b692d5c3a949234f81f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388040"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Środki zaradcze: Metoda X509CertificateClaimSet.FindClaims
Począwszy od aplikacji przeznaczonych [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda będzie próbował dopasować `claimType` argumentu z wszystkie wpisy DNS w polu sieci SAN.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana wpływa tylko na aplikacje, które odnoszą się do wersji programu .NET Framework począwszy [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 W przypadku aplikacji, które odnoszą się do poprzednich wersji programu .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda próbuje dopasować `claimType` argument tylko z ostatni wpis DNS.  
  
## <a name="mitigation"></a>Ograniczenie  
 Jeśli ta zmiana jest niepożądane, aplikacje których docelowe wersje programu .NET Framework, począwszy od [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] można zrezygnować z go, dodając następujące ustawienia konfiguracji do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) części aplikacji plik konfiguracji:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 Ponadto aplikacje docelowe poprzednie wersje programu .NET Framework, które działają w ramach [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] i nowszych wersjach zgodzić się na ten problem, dodając następujące ustawienia konfiguracji do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)sekcji pliku konfiguracji aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
