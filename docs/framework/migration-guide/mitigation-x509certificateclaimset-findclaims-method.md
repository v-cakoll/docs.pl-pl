---
title: 'Środki zaradcze: X509CertificateClaimSet.FindClaims Method'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccc24cd494866c087860144f1720988ccfc2dfa8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536441"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Środki zaradcze: X509CertificateClaimSet.FindClaims Method
Począwszy od aplikacji, których platformą docelową [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda będzie próbował dopasować `claimType` argument w przypadku wszystkich wpisów DNS w jego polu sieci SAN.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana dotyczy tylko aplikacji, przeznaczonych dla wersji programu .NET Framework począwszy od [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 W przypadku aplikacji przeznaczonych dla poprzednich wersji programu .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda próbuje dopasować `claimType` argumentu tylko ostatni wpis DNS.  
  
## <a name="mitigation"></a>Ograniczenie  
 Jeśli ta zmiana jest niepożądany, aplikacje, są przeznaczone dla wersji programu .NET Framework, począwszy od [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] można zrezygnować z go, dodając następujące ustawienie konfiguracji, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) części aplikacji plik konfiguracji:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 Ponadto aplikacje poprzedniej wersji programu .NET Framework, które są uruchomione w [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] i nowszych wersjach zgodzić się na to zachowanie, dodając następujące ustawienie konfiguracji, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)sekcję pliku konfiguracji aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz także
- [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
