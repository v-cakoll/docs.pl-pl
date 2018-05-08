---
title: Namespace mapowanie między WIF 3.5 i WIF 4.5
ms.date: 03/30/2017
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a120347d20de5b881ccb60d03da482856d9e68a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="namespace-mapping-between-wif-35-and-wif-45"></a>Namespace mapowanie między WIF 3.5 i WIF 4.5
Począwszy od platformy .NET 4.5, Windows Identity Foundation (WIF) zostało pełni zintegrowane programu .NET Framework. Integracja ta powstałe zmiany nazwy i niektóre konsolidacji WIF obszary nazw i powierzchni interfejsu API. Ten temat zawiera instrukcje oraz ogólne mapowania między przestrzenie nazw WIF 3.5 i przestrzenie nazw WIF 4.5. Nie ma być wyczerpujące, ale raczej Podaj ogólne informacje o tym, gdzie można znaleźć klasy WIF 3.5 znanych w wersji WIF 4.5. Aby uzyskać szczegółowe informacje o różnicach między WIF 3.5 i WIF 4.5, zobacz [What's New in Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md). Aby uzyskać wskazówki dotyczące migracji aplikacji utworzony za pomocą WIF 3.5 WIF 4.5, zobacz [wskazówki dotyczące migrowania aplikacji utworzony za pomocą programu WIF 3.5 WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
## <a name="wif-35-to-wif-45-namespace-map"></a>WIF 3.5 do wersji WIF 4.5 Namespace mapy  
 Klasy WIF, które zostały zebrane w ramach `Microsoft.IdentityModel` przestrzeni nazw w WIF 3.5, teraz są rozmieszczone w następujących przestrzeni nazw: `System.Security.Claims`, `System.ServiceModel.Security`i `System.IdentityModel` przestrzeni nazw w wersji WIF 4.5. Ponadto niektóre WIF 3.5 przestrzeni nazw zostały skonsolidowane lub porzucony w całości WIF 4.5.  
  
> [!IMPORTANT]
>  Następujące `System.IdentityModel` przestrzenie nazw zawiera klasy, które implementują modelu tożsamości opartego na oświadczeniach WCF: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, i <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Model zarządzania tożsamościami oparty na oświadczeniach stosowany w środowisku WCF jest zastąpiony modelem ze środowiska WIF. Nie należy używać klas w tych trzech obszarach nazw podczas tworzenia rozwiązań opartych na WIF.  
  
 Poniższa tabela zawiera informacje o którym klasy WIF 3.5 znajdują się w wersji WIF 4.5.  
  
|**WIF 3.5 Namespace**|**WIF 4.5 Namespace**|**Komentarze**|  
|-|-|-|  
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=nameWithType>|-Nie zaimplementowano większość klas, które reprezentują stałe.<br />-Klasy, które są używane do tworzenia usługi tokenu zabezpieczeń zostały przeniesione z `Microsoft.IdentityModel.SecurityTokenService` do <xref:System.IdentityModel?displayProperty=nameWithType>.<br />-Klas w `Microsoft.IdentityModel.Threading` zostały przeniesione do <xref:System.IdentityModel?displayProperty=nameWithType>.<br />- `ExceptionMapper` i `MruSecurityTokenCache` klasy nie jest zaimplementowana.|  
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=nameWithType>|- `IClaimsPrincipal` i `IClaimsIdentity` interfejsy nie są zaimplementowane w wersji WIF 4.5. Zamiast tego <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> i <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> są teraz klas podstawowych, z których większość .NET główna i pochodzi z klasy tożsamości. Oznacza to, nie jest konieczne specjalne oświadczenia podmiotu zabezpieczeń i tożsamość klas takich jak `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` i `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity` w wersji WIF 4.5, użyj <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> i <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> zamiast tego. To samo dotyczy dla innych dla innych specjalne oświadczenia podmiotu zabezpieczeń i tożsamości klasy, które były dostępne w programie WIF 3.5.<br />- `Microsoft.IdentityModel.Claims.ClaimsCollection` Klasy nie jest zaimplementowana w wersji WIF 4.5. Zamiast tego kolekcji oświadczenia są widoczne jako wyliczalny kolekcji tego typu <xref:System.Security.Claims.Claim?displayProperty=nameWithType>.<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> i <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> podania metod, które obecnie obsługują w pełni LINQ.|  
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=nameWithType>|Niektóre elementy i klasy przeszły zmiany nazwy i niektóre zostały usunięte w wersji WIF 4.5; na przykład `Microsoft.IdentityModel.Configuraiton.ServiceConfiguration` jest teraz <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=nameWithType>.|  
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Protocols.WSIdentity`|Nie zaimplementowano w wersji WIF 4.5|W WIF 3.5 zawiera klasy do obsługi CardSpace nie jest zaimplementowana w wersji WIF 4.5.|  
|`Microsoft.IdentityModel.Protocols.WSTrust`|Podzielony między <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> i <xref:System.ServiceModel.Security?displayProperty=nameWithType> przestrzeni nazw.|Klasy reprezentujące artefakty WS-Trust znajdują się w <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> przestrzeni nazw, na przykład <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken> klasy. Klasy reprezentujące kontraktów usług WCF, hosty usługi i kanałów, które umożliwiają usługi WCF w celu komunikowania się przy użyciu protokołu WS-Trust znajdują się w <xref:System.ServiceModel.Security?displayProperty=nameWithType> przestrzeni nazw, na przykład <xref:System.ServiceModel.Security.WSTrustServiceHost> klasy.|  
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|Nie zaimplementowano w wersji WIF 4.5|-|  
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|Nie zaimplementowano w wersji WIF 4.5|Zawiera klasy reprezentujące stałe szyfrowanie XML w WIF 3.5. Stałe te nie są zaimplementowane w wersji WIF 4.5.|  
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=nameWithType>|`EnvelopingSignature` Klasa i klasy, które reprezentują stałe nie są zaimplementowane.|  
|`Microsoft.IdentityModel.SecurityTokenService`|Podzielony między <xref:System.IdentityModel?displayProperty=nameWithType>, <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>, i <xref:System.IdentityModel.Tokens?displayProperty=nameWithType> przestrzeni nazw.|-|  
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>|Klasy, które zapewniają konfigurację dla pasywnych scenariuszy (WS-Federation) przede wszystkim zostały przeniesione do <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>, jednak niektóre z tych klas są <xref:System.IdentityModel.Services?displayProperty=nameWithType>.|  
|`Microsoft.IdentityModel.Web.Controls`|Nie zaimplementowano w wersji WIF 4.5|Klasy w `Microsoft.IdentityModel.Web.Controls` zaimplementowana federacyjnych pasywnym logowania formantu, który nie istnieje w wersji WIF 4.5.|  
|`Microsoft.IdentityModel.WindowsTokenService`|Nie zaimplementowano w wersji WIF 4.5|-|  
  
## <a name="see-also"></a>Zobacz też  
 [Co nowego w programie Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md)  
 [Wskazówki dotyczące migrowania aplikacji utworzonych za pomocą programu WIF 3.5 do wersji WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
