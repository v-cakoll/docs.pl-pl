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
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Środki zaradcze: X509CertificateClaimSet.FindClaims Method
Począwszy od aplikacji przeznaczonych dla platformy .NET Framework 4.6.1, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda będzie próbował dopasować `claimType` argument w przypadku wszystkich wpisów DNS w jego polu sieci SAN.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana dotyczy tylko aplikacji, przeznaczonych dla wersji programu .NET Framework, począwszy od programu .NET Framework 4.6.1.  
  
 W przypadku aplikacji przeznaczonych dla poprzednich wersji programu .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda próbuje dopasować `claimType` argumentu tylko ostatni wpis DNS.  
  
## <a name="mitigation"></a>Ograniczenie  
 Jeśli ta zmiana jest niepożądany, aplikacji przeznaczonych dla wersji programu .NET Framework, począwszy od programu .NET Framework 4.6.1 można zrezygnować z go, dodając następujące ustawienie konfiguracji, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji plik konfiguracji aplikacji:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 Ponadto aplikacje poprzedniej wersji programu .NET Framework, które są uruchomione w .NET Framework 4.6.1 i nowszych wersjach zgodzić się na to zachowanie, dodając następujące ustawienie konfiguracji, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcję pliku konfiguracji aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
