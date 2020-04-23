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
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Łagodzenie: X509CertificateClaimSet.FindClaims Metoda

Począwszy od aplikacji docelowych .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> 4.6.1, `claimType` metoda będzie próbować dopasować argument do wszystkich wpisów DNS w polu SAN.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana dotyczy tylko aplikacji, które docelowe wersje programu .NET Framework, począwszy od programu .NET Framework 4.6.1.  
  
 W przypadku aplikacji przeznaczonych dla poprzednich <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> wersji programu .NET Framework metoda próbuje dopasować `claimType` argument tylko do ostatniego wpisu DNS.  
  
## <a name="mitigation"></a>Środki zaradcze  
 Jeśli ta zmiana jest niepożądana, aplikacje docelowe wersji programu .NET Framework, począwszy od programu .NET Framework 4.6.1, mogą zrezygnować z niej, dodając następujące ustawienie konfiguracji do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracyjnego aplikacji:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 Ponadto aplikacje przeznaczone dla poprzednich wersji programu .NET Framework, ale uruchomione w ramach programu .NET Framework 4.6.1 i nowszych wersji mogą zdecydować się na to zachowanie, dodając następujące ustawienie konfiguracji do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracyjnego aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
