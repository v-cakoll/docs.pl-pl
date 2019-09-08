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
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Środki zaradcze X509CertificateClaimSet.FindClaims Method
Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6.1 <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> , Metoda podejmie próbę `claimType` dopasowania argumentu ze wszystkimi wpisami DNS w jego polu sieci SAN.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana ma wpływ tylko na aplikacje, które są przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1.  
  
 W przypadku aplikacji przeznaczonych dla poprzednich wersji .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> Metoda próbuje `claimType` dopasować argument tylko do ostatniego wpisu DNS.  
  
## <a name="mitigation"></a>Ograniczenie  
 Jeśli ta zmiana jest niepożądana, aplikacje przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1 mogą zrezygnować z niego, dodając następujące ustawienia konfiguracji do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracji aplikacji :  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework ale działają w ramach .NET Framework 4.6.1 i nowszych wersji, mogą zrezygnować z tego zachowania, dodając następujące ustawienia konfiguracji do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) plik konfiguracji aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](retargeting-changes-in-the-net-framework-4-6-1.md)
