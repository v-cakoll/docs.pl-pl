---
title: Dokumentacja interfejsu API WIF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e3209ac32314e2ac3f4e3e1920991ed29f956832
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wif-api-reference"></a>Dokumentacja interfejsu API WIF
Klasy Windows Identity Foundation (WIF) są podzielone między następujące zestawy: `mscorlib` (mscorlib.dll) `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll) i `System.ServiceModel` () System.ServiceModel.dll). Ten temat zawiera linki do WIF obszary nazw i klasy, które każda przestrzeń nazw zawiera krótkie objaśnienia.  
  
> [!IMPORTANT]
>  Następujące `System.IdentityModel` przestrzenie nazw zawiera klasy, które implementują modelu tożsamości opartego na oświadczeniach WCF: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, i <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Począwszy od programu .NET Framework 4.5, usługi WCF modelu tożsamości opartego na oświadczeniach zostało zastąpione przez WIF. Nie należy używać klas w tych trzech obszarach nazw podczas tworzenia rozwiązań opartych na WIF.  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące transformacje plików cookie, usługi tokenu zabezpieczeń i specjalnych czytników słownika XML.  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 Zawiera klasy udostępniające konfiguracji dla aplikacji i usług, utworzony przy użyciu systemu Windows Identity Foundation (WIF). Ustawienia w obszarze reprezentują klasy w tej przestrzeni nazw [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące elementów w dokumencie metadanych federacji.  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące artefakty WS-Trust.  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 Zawiera klasy, które są używane w scenariuszach, pasywnym (WS-Federation). Zawiera także niektóre klasy, które reprezentują ustawienia w obszarze [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) elementu. Ustawienia w tym elemencie Konfigurowanie protokołu WS-Federation dla aplikacji. `System.IdentityModel.Services.Configuration` Przestrzeń nazw zawiera większość klas, które są używane do konfigurowania usługi WS-Federation.  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 Zawiera klasy udostępniające konfigurowania WIF aplikacji, które korzystają z protokołu WS-Federation. Ustawienia w obszarze reprezentują klasy w tej przestrzeni nazw [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) elementu. `System.IdentityModel.Services` Przestrzeń nazw zawiera także niektóre klasy, które są używane do konfigurowania usługi WS-Federation.  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 Zawiera token obsługi specjalnych zabezpieczeń na scenariusze farmy sieci Web.  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące tokeny zabezpieczające, obsługi tokenu zabezpieczeń i innych artefaktów tokenu zabezpieczeń.  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące oświadczeń, tożsamości opartego na oświadczeniach podmiotów opartego na oświadczeniach i pozostałych artefaktów modelu tożsamości opartego na oświadczeniach.  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące WCF kontrakty, kanały, hosty usługi i pozostałych artefaktów, które są używane w scenariuszach (WS-Trust) active. Ta przestrzeń nazw zawiera również klasy specyficznych do usługi Windows Communication Foundation (WCF) i które nie są używane przez WIF.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie konfiguracji programu WIF](../../../docs/framework/security/wif-configuration-reference.md)  
 [Mapowanie przestrzeni nazw między programami WIF 3.5 i WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
