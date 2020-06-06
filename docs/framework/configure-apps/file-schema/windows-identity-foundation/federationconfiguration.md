---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: bcd8e00b770517e3faff011b4acee08ebdc5a0df
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152739"
---
# \<federationConfiguration>
Konfiguruje <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (sam), gdy jest używane uwierzytelnianie federacyjne za pośrednictwem protokołu WS-Federation. Konfiguruje <xref:System.Security.Claims.ClaimsAuthorizationManager> podczas korzystania z <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<federationConfiguration>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|name|Nazwa tego elementu konfiguracji federacyjnej. Ten atrybut obejmuje głównie punkt rozszerzalności dla przyszłych protokołów. Opcjonalny.|  
|identityConfigurationName|Nazwa sekcji konfiguracji tożsamości określona w [\<identityConfiguration>](identityconfiguration.md) elemencie do użycia. Jeśli ten atrybut nie jest określony, zostanie użyta domyślna sekcja konfiguracji tożsamości. Opcjonalny.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|Konfiguruje obsługę plików cookie używaną przez SAM. Opcjonalny.|  
|[\<serviceCertificate>](servicecertificate.md)|Konfiguruje certyfikat używany do szyfrowania i odszyfrowywania tokenów. Opcjonalny.|  
|[\<wsFederation>](wsfederation.md)|Konfiguruje moduł uwierzytelniania WS-Federation (WSFAM). Opcjonalny.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|Sekcja konfiguracji uwierzytelniania przy użyciu protokołu WS-Federation.|  
  
## <a name="remarks"></a>Uwagi  
 \<federationConfiguration>Element zawiera ustawienia w dwóch różnych scenariuszach:  
  
- W przypadku korzystania z protokołu WS-Federation w pasywnej aplikacji sieci Web element zawiera ustawienia, które konfigurują <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (sam). Odwołuje się on również do konfiguracji tożsamości, która będzie używana do konfigurowania obsługi tokenów zabezpieczających i certyfikatów oraz składników, takich jak Menedżer autoryzacji oświadczeń i Menedżer uwierzytelniania oświadczeń.  
  
- W przypadku użycia <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie element odwołuje się do konfiguracji tożsamości, która konfiguruje Menedżera autoryzacji oświadczeń i zasady, które są używane w celu podejmowania decyzji dotyczących autoryzacji. Jest to prawdziwe, nawet w scenariuszach, które nie są pasywnymi scenariuszami sieci Web. na przykład aplikacje Windows Communication Foundation (WCF) lub aplikacja, która nie jest oparta na sieci Web. Jeśli aplikacja nie jest pasywną aplikacją sieci Web, [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (i jego elementy zasad podrzędnych, jeśli istnieją) konfiguracji tożsamości, do której odwołuje się `<federationConfiguration>` element, są jedynymi stosowanymi ustawieniami. Wszystkie pozostałe są ignorowane.  
  
 Niezależnie od scenariusza środowisko uruchomieniowe ładuje domyślną konfigurację Federacji. Zachowanie jest zdefiniowane w następujący sposób:  
  
1. Jeśli nie ma żadnego `<federationConfiguration>` elementu, środowisko uruchomieniowe tworzy konfigurację Federacji i wypełnia je wartościami domyślnymi. Ta domyślna konfiguracja federacji będzie odwoływać się do domyślnej konfiguracji tożsamości.  
  
2. Jeśli jest `<federationConfiguration>` obecny pojedynczy element, jest to domyślna konfiguracja federacji bez względu na to, czy ma ona nazwę, czy nie. Jeśli jego `identityConfiguration` atrybut jest określony, przywoływana jest Konfiguracja tożsamości nazwanej; w przeciwnym razie jest przywoływana domyślna konfiguracja tożsamości.  
  
3. Jeśli istnieje nienazwany `<federationConfiguration>` element, jest to domyślna konfiguracja federacji. Jeśli jego `identityConfiguration` atrybut jest określony, przywoływana jest Konfiguracja tożsamości nazwanej; w przeciwnym razie jest przywoływana domyślna konfiguracja tożsamości.  
  
4. Jeśli istnieje wiele nazwanych `<federationConfiguration>` elementów i nie ma elementu bez nazwy `<federationConfiguration>` , zgłaszany jest wyjątek.  
  
 Zwykle zdefiniowana jest tylko jedna `<federationConfiguration>` sekcja. Ta sekcja jest domyślną konfiguracją Federacji. Można określić wiele elementów o unikatowej nazwie, `<federationConfiguration>` jednak w tym przypadku, jeśli chcesz załadować konfigurację Federacji inną niż nazwa, należy podać procedurę obsługi dla. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>zdarzenie i ustawienie <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> Właściwości wewnątrz procedury obsługi na <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> obiekt zainicjowany z wartościami z odpowiedniego `<federationConfiguration>` elementu w pliku konfiguracji.  
  
 `<federationConfiguration>`Element jest reprezentowany przez <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> klasę. Sam obiekt konfiguracji jest reprezentowany przez <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> klasę. Pojedyncze <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> wystąpienie jest ustawione dla <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> właściwości i zapewnia konfigurację federacyjną dla aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XML przedstawia `<federationConfiguration>` element określający ustawienia dla WSFAM i określa, że domyślny program obsługi plików cookie (wystąpienie <xref:System.IdentityModel.Services.ChunkedCookieHandler> klasy) będzie używany przez sam.  
  
> [!WARNING]
> W tym przykładzie żadna procedura obsługi plików cookie i WSFAM nie jest wymagana do korzystania z protokołu HTTPS. Jest to spowodowane tym, że `requireHttps` atrybut `<wsFederation>` elementu i `requireSsl` atrybutu na `<cookieHandlerElement>` `false` . Te ustawienia nie są zalecane w przypadku większości środowisk produkcyjnych, ponieważ mogą one stanowić zagrożenie dla bezpieczeństwa.  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation passiveRedirectEnabled="true"
      issuer="http://localhost:15839/wsFederationSTS/Issue"
      realm="http://localhost:50969/" reply="http://localhost:50969/"
      requireHttps="false"
      signOutReply="http://localhost:50969/SignedOutPage.html"
      signOutQueryString="Param1=value2&Param2=value2"
      persistentCookiesOnPassiveRedirects="true" />  
    <cookieHandler requireSsl="false" />  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<identityConfiguration>](identityconfiguration.md)
