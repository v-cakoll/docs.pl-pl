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
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Ograniczanie: X509CertificateClaimSet. FindClaims Metoda

Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6.1, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> Metoda podejmie próbę dopasowania `claimType` argumentu ze wszystkimi wpisami DNS w jego polu sieci SAN.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana ma wpływ tylko na aplikacje, które są przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1.  
  
 W przypadku aplikacji przeznaczonych dla poprzednich wersji .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> Metoda próbuje dopasować `claimType` argument tylko do ostatniego wpisu DNS.  
  
## <a name="mitigation"></a>Ograniczanie ryzyka  
 Jeśli ta zmiana jest niepożądana, aplikacje przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1 mogą zrezygnować z niego, dodając następujące ustawienia konfiguracji do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework ale działają w ramach .NET Framework 4.6.1 i nowszych wersji, mogą zrezygnować z tego zachowania, dodając następujące ustawienia konfiguracji do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
