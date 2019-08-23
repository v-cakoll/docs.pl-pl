---
title: Dokumentacja interfejsu API programu WIF
ms.date: 03/30/2017
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
author: BrucePerlerMS
ms.openlocfilehash: 17a1da0a3b0ea6567fd805e7273f793ace35ae69
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958345"
---
# <a name="wif-api-reference"></a>Dokumentacja interfejsu API programu WIF
Klasy Windows Identity Foundation (WIF) są podzielone `mscorlib` na następujące zestawy: (mscorlib. dll), `System.IdentityModel` (System. IdentityModel. dll), `System.IdentityModel.Services` (System. IdentityModel. Services. dll) i `System.ServiceModel` ( System. ServiceModel. dll). Ten temat zawiera linki do przestrzeni nazw WIF oraz krótkie wyjaśnienia dotyczące klas, które zawierają poszczególne obszary nazw.  
  
> [!IMPORTANT]
> Następujące `System.IdentityModel` przestrzenie nazw zawierają klasy implementujące model tożsamości oparty na oświadczeniach WCF <xref:System.IdentityModel.Claims?displayProperty=nameWithType>: <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, i <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Począwszy od .NET Framework 4,5, model tożsamości oparty na oświadczeniach WCF jest zastępowany przez WIF. Nie należy używać klas w tych trzech przestrzeniach nazw podczas kompilowania rozwiązań opartych na WIF.  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące przekształcenia plików cookie, usługi tokenów zabezpieczających i wyspecjalizowane czytniki słownika XML.  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 Zawiera klasy, które zapewniają konfigurację dla aplikacji i usług utworzonych przy użyciu programu Windows Identity Foundation (WIF). Klasy w tej przestrzeni nazw reprezentują ustawienia w [ \<elemencie IdentityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) .  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 Zawiera klasy, które reprezentują elementy w dokumencie metadanych Federacji.  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące artefakty protokołu WS-Trust.  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 Zawiera klasy, które są używane w scenariuszach pasywnych (WS-Federation). Zawiera również klasy, które reprezentują ustawienia w ramach [ \<elementu > System. IdentityModel. Services](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) . Ustawienia w obszarze tego elementu Konfigurowanie usługi WS-Federation dla aplikacji. `System.IdentityModel.Services.Configuration` Przestrzeń nazw zawiera większość klas, które są używane do konfigurowania usługi WS-Federation.  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 Zawiera klasy, które zapewniają konfigurację dla aplikacji WIF korzystających z protokołu WS-Federation. Klasy w tej przestrzeni nazw reprezentują ustawienia w ramach [ \<elementu > System. IdentityModel. Services](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) . `System.IdentityModel.Services` Przestrzeń nazw zawiera również kilka klas, które są używane do konfigurowania usługi WS-Federation.  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 Zawiera wyspecjalizowane programy obsługi tokenów zabezpieczeń dla scenariuszy farmy sieci Web.  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące tokeny zabezpieczające, programy obsługi tokenów zabezpieczających i inne artefakty tokenów zabezpieczających.  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące oświadczenia, tożsamości oparte na oświadczeniach, podmioty zabezpieczeń oparte na oświadczeniach i inne artefakty modelu tożsamości oparte na oświadczeniach.  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 Zawiera klasy, które reprezentują kontrakty WCF, kanały, hosty usług i inne artefakty, które są używane w scenariuszach Active (WS-Trust). Ta przestrzeń nazw zawiera również klasy, które są specyficzne dla Windows Communication Foundation (WCF) i które nie są używane przez WIF.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie konfiguracji programu WIF](../../../docs/framework/security/wif-configuration-reference.md)
- [Mapowanie przestrzeni nazw między programami WIF 3.5 i WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
