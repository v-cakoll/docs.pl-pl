---
title: Mapowanie przestrzeni nazw między programami WIF 3.5 i WIF 4.5
ms.date: 03/30/2017
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
author: BrucePerlerMS
ms.openlocfilehash: ef5801ccfdda22b1c89c22ea9c2b14ea0855ed26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670036"
---
# <a name="namespace-mapping-between-wif-35-and-wif-45"></a>Mapowanie przestrzeni nazw między programami WIF 3.5 i WIF 4.5

Począwszy od .NET 4.5, Windows Identity Foundation (WIF) zostało w pełni zintegrowane programu .NET Framework. Ta integracja przewidywanymi zmiany nazwy i niektóre konsolidacji przestrzeniach nazw środowiska WIF oraz powierzchni interfejsu API. Ten temat zawiera wskazówki i ogólne mapowanie między przestrzenie nazw WIF 3.5 i WIF 4.5 przestrzeni nazw. Nie ma być wyczerpujące, ale raczej zapewnienia ogólne informacje o tym, gdzie można znaleźć znanych klasy programu WIF 3.5 w programie WIF 4.5. Aby uzyskać więcej informacji o różnicach między WIF 3.5 i WIF 4.5, zobacz [What's New in Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md). Aby uzyskać wskazówki dotyczące sposobu przeprowadzania migracji aplikacji utworzonych przy użyciu programu WIF 3.5 to WIF 4.5, zobacz [Guidelines for Migrating an Application Built Using WIF 3.5 to WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).

## <a name="wif-35-to-wif-45-namespace-map"></a>Program WIF 3.5 do programu WIF 4.5 Namespace mapy

Klasy programu WIF, które zostały zebrane w ramach `Microsoft.IdentityModel` przestrzeniach nazw programu WIF 3.5 są obecnie dystrybuowane między następujących przestrzeni nazw: `System.Security.Claims`, `System.ServiceModel.Security`i `System.IdentityModel` przestrzeniach nazw programu WIF 4.5. Ponadto niektóre przestrzenie nazw WIF 3.5 zostały skonsolidowane lub porzucony w całości WIF 4.5.

> [!IMPORTANT]
> Następujące `System.IdentityModel` przestrzenie nazw zawierają klasy, które implementują modelu tożsamości opartej na oświadczeniach WCF: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, i <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Model zarządzania tożsamościami oparty na oświadczeniach stosowany w środowisku WCF jest zastąpiony modelem ze środowiska WIF. Nie należy używać klas w tych trzech przestrzeni nazw, podczas tworzenia rozwiązań opartych na programu WIF.

Poniższa tabela zawiera informacje o gdzie można znaleźć klasy programu WIF 3.5 w programie WIF 4.5.

|**Program WIF 3.5 Namespace**|**Program WIF 4.5 Namespace**|**Komentarze**|
|-|-|-|
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=nameWithType>|— Większość klas, które reprezentują stałe nie są zaimplementowane.<br />-Klasy, które są używane do tworzenia usługi tokenów zabezpieczeń zostały przeniesione z `Microsoft.IdentityModel.SecurityTokenService` do <xref:System.IdentityModel?displayProperty=nameWithType>.<br />-Klasy w `Microsoft.IdentityModel.Threading` zostały przeniesione do ikony <xref:System.IdentityModel?displayProperty=nameWithType>.<br />`ExceptionMapper` i `MruSecurityTokenCache` klasy nie są zaimplementowane.|
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=nameWithType>|`IClaimsPrincipal` i `IClaimsIdentity` interfejsy nie są implementowane w WIF 4.5. Zamiast tego <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> i <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> są teraz klas bazowych, z których większość .NET podmiotu zabezpieczeń i tożsamości klas pochodnych. Oznacza to, że nie ma potrzeby oświadczenia wyspecjalizowane klasy podmiot zabezpieczeń i tożsamości, takie jak `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` i `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity` w program WIF 4.5, za pomocą <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> i <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> zamiast tego. To samo dotyczy dla innych dla innych wyspecjalizowane oświadczenia podmiotu zabezpieczeń i tożsamości klas, które istniały w WIF 3.5.<br />`Microsoft.IdentityModel.Claims.ClaimsCollection` Klasy nie jest zaimplementowana w WIF 4.5. Zamiast tego kolekcje oświadczenia są widoczne jako przeliczalne kolekcje typu <xref:System.Security.Claims.Claim?displayProperty=nameWithType>.<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> i <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> podania metod, które teraz obsługują w pełni LINQ.|
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=nameWithType>|Niektóre klasy i elementy zostały poddane zmiany nazwy, a niektóre zostały usunięte w programie WIF 4.5; na przykład `Microsoft.IdentityModel.Configuration.ServiceConfiguration` jest teraz <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=nameWithType>.|
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSIdentity`|Nie jest zaimplementowana w programu WIF 4.5|W programu WIF 3.5 zawiera klasy do obsługi CardSpace, nie jest zaimplementowana w WIF 4.5.|
|`Microsoft.IdentityModel.Protocols.WSTrust`|Podzielony między <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> i <xref:System.ServiceModel.Security?displayProperty=nameWithType> przestrzeni nazw.|Należą do klasy reprezentujące artefaktów WS-Trust <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> przestrzeni nazw, na przykład <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken> klasy. Należą do klasy, które reprezentują kontraktów usług WCF, hosty usług i kanałów, które umożliwiają usługi WCF do komunikowania się za pomocą protokołu WS-Trust <xref:System.ServiceModel.Security?displayProperty=nameWithType> przestrzeni nazw, na przykład <xref:System.ServiceModel.Security.WSTrustServiceHost> klasy.|
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|Nie jest zaimplementowana w programu WIF 4.5|-|
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|Nie jest zaimplementowana w programu WIF 4.5|Zawiera klasy, które reprezentują stałe szyfrowanie XML w WIF 3.5. Te stałe są niedostępne w WIF 4.5.|
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=nameWithType>|`EnvelopingSignature` Klasy i klas, które reprezentują stałe są niedostępne.|
|`Microsoft.IdentityModel.SecurityTokenService`|Podzielony między <xref:System.IdentityModel?displayProperty=nameWithType>, <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>, i <xref:System.IdentityModel.Tokens?displayProperty=nameWithType> przestrzeni nazw.|-|
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>|Klasy, które zapewniają konfiguracji dla większości pasywnym scenariuszy (WS-Federation) zostały przeniesione do ikony <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>; jednak niektóre z tych klas są <xref:System.IdentityModel.Services?displayProperty=nameWithType>.|
|`Microsoft.IdentityModel.Web.Controls`|Nie jest zaimplementowana w programu WIF 4.5|Klasy w `Microsoft.IdentityModel.Web.Controls` zaimplementowane federacyjnych pasywnym logowania kontrolki, które nie istnieje w WIF 4.5.|
|`Microsoft.IdentityModel.WindowsTokenService`|Nie jest zaimplementowana w programu WIF 4.5|-|

## <a name="see-also"></a>Zobacz także

- [Co nowego w programie Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md)
- [Wskazówki dotyczące migrowania aplikacji utworzonych za pomocą programu WIF 3.5 do wersji WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
