---
title: Dokumentacja interfejsu API programu WIF
ms.date: 03/30/2017
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
author: BrucePerlerMS
ms.openlocfilehash: c94ccd3f25be576c57fda798c6b2b8cc25357022
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172214"
---
# <a name="wif-api-reference"></a>Dokumentacja interfejsu API programu WIF
Klasy Windows Identity Foundation (WIF) są dzielone między następujących zestawów: `mscorlib` (mscorlib.dll) `System.IdentityModel` (System.IdentityModel.dll) `System.IdentityModel.Services` (System.IdentityModel.Services.dll) i `System.ServiceModel` () System.ServiceModel.dll). Ten temat zawiera łącza do przestrzeniach nazw środowiska WIF i krótkie objaśnienia klas, które zawiera każdej przestrzeni nazw.  
  
> [!IMPORTANT]
>  Następujące `System.IdentityModel` przestrzenie nazw zawierają klasy, które implementują modelu tożsamości opartej na oświadczeniach WCF: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, i <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Począwszy od programu .NET Framework 4.5, modelu tożsamości opartej na oświadczeniach WCF jest zastąpiony programu WIF. Nie należy używać klas w tych trzech przestrzeni nazw, podczas tworzenia rozwiązań opartych na programu WIF.  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące transformacje pliku cookie, usługi tokenu zabezpieczeń i wyspecjalizowane czytelników słownika XML.  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 Zawiera klasy udostępniające konfiguracji dla aplikacji i usług utworzonych przy użyciu Windows Identity Foundation (WIF). Klasy w tej przestrzeni nazw reprezentuje ustawienia w obszarze [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące elementy dokumentu metadanych federacji.  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące artefaktów WS-Trust.  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 Zawiera klasy, które są używane w scenariuszach usługi pasywnym (WS-Federation). Zawiera także kilka klas, które reprezentują ustawienia w obszarze [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) elementu. Ustawienia w obszarze tego elementu skonfigurować WS-Federation na potrzeby aplikacji. `System.IdentityModel.Services.Configuration` Przestrzeń nazw zawiera większość klas, które są używane do konfigurowania protokołu WS-Federation.  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 Zawiera klasy udostępniające konfiguracji dla aplikacji programu WIF, które używają protokołu WS-Federation. Klasy w tej przestrzeni nazw reprezentuje ustawienia w obszarze [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) elementu. `System.IdentityModel.Services` Przestrzeń nazw zawiera także niektórych klas, które są używane do konfigurowania protokołu WS-Federation.  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 Zawiera wyspecjalizowanych zabezpieczeń programy obsługi tokenów sieci Web na scenariusze farmy.  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące tokeny zabezpieczające, programy obsługi tokenów zabezpieczających i innych artefaktów tokenu zabezpieczeń.  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące oświadczeń, tożsamości opartej na oświadczeniach, opartej na oświadczeniach podmiotów zabezpieczeń i inne artefakty modelu tożsamości opartej na oświadczeniach.  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 Zawiera klasy reprezentujące WCF umów, kanałów i hosty usług oraz innych artefaktów, które są używane w aktywnej scenariuszy (WS-Trust). Ta przestrzeń nazw zawiera także klas specyficznych do programu Windows Communication Foundation (WCF) i które nie są używane przez program WIF.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie konfiguracji programu WIF](../../../docs/framework/security/wif-configuration-reference.md)
- [Mapowanie przestrzeni nazw między programami WIF 3.5 i WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
