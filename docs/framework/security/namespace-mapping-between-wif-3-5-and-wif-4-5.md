---
title: Mapowanie przestrzeni nazw między programami WIF 3.5 i WIF 4.5
ms.date: 03/30/2017
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
author: BrucePerlerMS
ms.openlocfilehash: d967ce931e81ca14645e7464943e1411264d6ca2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045401"
---
# <a name="namespace-mapping-between-wif-35-and-wif-45"></a>Mapowanie przestrzeni nazw między programami WIF 3.5 i WIF 4.5

Począwszy od programu .NET 4,5, Windows Identity Foundation (WIF) został w pełni zintegrowany z .NET Framework. Ta nazwa integracji engendered ulega zmianie i pewnej konsolidacji przestrzeni nazw WIF i powierzchni interfejsu API. Ten temat zawiera wskazówki i ogólne mapowanie między przestrzeniami nazw WIF 3,5 a przestrzeniami nazw WIF 4,5. Nie jest on przeznaczony do wyczerpującego, ale udostępniamy ogólne informacje o tym, gdzie znaleźć znane klasy WIF 3,5 w WIF 4,5. Aby uzyskać bardziej szczegółowe informacje na temat różnic między WIF 3,5 i WIF 4,5, zobacz [co nowego w programie Windows Identity Foundation 4,5](whats-new-in-wif.md). Aby uzyskać wskazówki dotyczące sposobu migracji aplikacji utworzonych przy użyciu WIF 3,5 do WIF 4,5, zobacz [wytyczne dotyczące migrowania aplikacji utworzonej przy użyciu WIF 3,5 do WIF 4,5](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).

## <a name="wif-35-to-wif-45-namespace-map"></a>Mapa nazw WIF 3,5 WIF 4,5

Klasy WIF, które zostały `Microsoft.IdentityModel` zebrane w obszarze przestrzenie nazw w WIF 3,5, są teraz dystrybuowane między następujące przestrzenie nazw: `System.Security.Claims`, `System.IdentityModel` `System.ServiceModel.Security`i przestrzenie nazw w WIF 4,5. Ponadto niektóre przestrzenie nazw WIF 3,5 zostały skonsolidowane lub usunięte całkowicie w WIF 4,5.

> [!IMPORTANT]
> Następujące `System.IdentityModel` przestrzenie nazw zawierają klasy implementujące model tożsamości oparty na oświadczeniach WCF <xref:System.IdentityModel.Claims?displayProperty=nameWithType>: <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, i <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Model zarządzania tożsamościami oparty na oświadczeniach stosowany w środowisku WCF jest zastąpiony modelem ze środowiska WIF. Nie należy używać klas w tych trzech przestrzeniach nazw podczas kompilowania rozwiązań opartych na WIF.

Poniższa tabela zawiera informacje o tym, gdzie WIF 3,5 klasy można znaleźć w WIF 4,5.

|**WIF 3,5 — przestrzeń nazw**|**WIF 4,5 — przestrzeń nazw**|**Komentarze**|
|-|-|-|
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=nameWithType>|-Większość klas reprezentujących stałe nie jest zaimplementowana.<br />-Klasy, które są używane do tworzenia usług tokenów zabezpieczających, zostały `Microsoft.IdentityModel.SecurityTokenService` przeniesione <xref:System.IdentityModel?displayProperty=nameWithType>z do.<br />-Klasy w programie `Microsoft.IdentityModel.Threading` zostały przeniesione do. <xref:System.IdentityModel?displayProperty=nameWithType><br />-Nie zaimplementowano klas `MruSecurityTokenCache` i.`ExceptionMapper`|
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=nameWithType>|-Interfejsy `IClaimsIdentity` i nie są zaimplementowane w WIF 4,5. `IClaimsPrincipal` Zamiast <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> tego <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> i są teraz klasami bazowymi, z których pochodzą większość głównych klas i tożsamości platformy .NET. Oznacza to, że nie ma potrzeby wyspecjalizowanych klas podmiotu zabezpieczeń i `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` tożsamości `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity` , takich jak i w <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> WIF <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> 4,5, używaj i zamiast tego. Ta sama wartość dotyczy innych wyspecjalizowanych podmiotów zabezpieczeń i klas tożsamości, które istniały w WIF 3,5.<br />`Microsoft.IdentityModel.Claims.ClaimsCollection` -Klasa nie jest zaimplementowana w WIF 4,5. Zamiast tego kolekcje oświadczeń są ujawniane jako wyliczalne kolekcje <xref:System.Security.Claims.Claim?displayProperty=nameWithType>typu.<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>i <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> zapewniają metody, które teraz w pełni obsługują LINQ.|
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=nameWithType>|Niektóre elementy i klasy zostały poddane zmianom nazw, a niektóre zostały usunięte w WIF 4,5; na przykład `Microsoft.IdentityModel.Configuration.ServiceConfiguration` teraz <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=nameWithType>.|
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSIdentity`|Nie zaimplementowane w WIF 4,5|W programie WIF 3,5 zawarte klasy obsługujące program CardSpace nie zostały zaimplementowane w WIF 4,5.|
|`Microsoft.IdentityModel.Protocols.WSTrust`|Podziel między <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> przestrzeniami <xref:System.ServiceModel.Security?displayProperty=nameWithType> nazw i.|Klasy reprezentujące artefakty protokołu WS-Trust znajdują się w <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> przestrzeni nazw, na przykład <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken> w klasie. Klasy reprezentujące kontrakty usługi WCF, hosty usług i kanały, które umożliwiają komunikację usługi WCF przy użyciu protokołu WS-Trust, znajdują <xref:System.ServiceModel.Security?displayProperty=nameWithType> się w przestrzeni nazw, na <xref:System.ServiceModel.Security.WSTrustServiceHost> przykład w klasie.|
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|Nie zaimplementowane w WIF 4,5|-|
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|Nie zaimplementowane w WIF 4,5|Zawarte klasy reprezentujące stałe szyfrowania XML w WIF 3,5. Te stałe nie są zaimplementowane w WIF 4,5.|
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=nameWithType>|`EnvelopingSignature` Klasy i klasy reprezentujące stałe nie są implementowane.|
|`Microsoft.IdentityModel.SecurityTokenService`|Podziel między <xref:System.IdentityModel?displayProperty=nameWithType>przestrzeniami <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>nazw, <xref:System.IdentityModel.Tokens?displayProperty=nameWithType> i.|-|
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>|Klasy, które zapewniają konfigurację dla pasywnych scenariuszy (WS-Federation), zostały przesunięte do <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>, jednak niektóre z tych klas znajdują się w. <xref:System.IdentityModel.Services?displayProperty=nameWithType>|
|`Microsoft.IdentityModel.Web.Controls`|Nie zaimplementowane w WIF 4,5|Klasy w `Microsoft.IdentityModel.Web.Controls` zaimplementowanej pasywnej kontrolce logowania jednokrotnego, która nie istnieje w WIF 4,5.|
|`Microsoft.IdentityModel.WindowsTokenService`|Nie zaimplementowane w WIF 4,5|-|

## <a name="see-also"></a>Zobacz także

- [Co nowego w programie Windows Identity Foundation 4.5](whats-new-in-wif.md)
- [Wskazówki dotyczące migrowania aplikacji utworzonych za pomocą programu WIF 3.5 do wersji WIF 4.5](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
