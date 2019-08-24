---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: c4dbb31bb7961f0d33df9d1faee8fe36ecb520a3
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988329"
---
# <a name="federationconfiguration"></a>\<federationConfiguration>
<xref:System.IdentityModel.Services.SessionAuthenticationModule> Konfiguruje <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i (sam), gdy jest używane uwierzytelnianie federacyjne za pośrednictwem protokołu WS-Federation. Konfiguruje <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> podczas korzystania z lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach. <xref:System.Security.Claims.ClaimsAuthorizationManager>  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
  
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
|nazwa|Nazwa tego elementu konfiguracji federacyjnej. Ten atrybut obejmuje głównie punkt rozszerzalności dla przyszłych protokołów. Opcjonalny.|  
|identityConfigurationName|Nazwa sekcji konfiguracji tożsamości określona w [ \<elemencie IdentityConfiguration >](identityconfiguration.md) do użycia. Jeśli ten atrybut nie jest określony, zostanie użyta domyślna sekcja konfiguracji tożsamości. Opcjonalny.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|Konfiguruje obsługę plików cookie używaną przez SAM. Opcjonalny.|  
|[\<> serviceCertificate](servicecertificate.md)|Konfiguruje certyfikat używany do szyfrowania i odszyfrowywania tokenów. Opcjonalna.|  
|[\<wsFederation>](wsfederation.md)|Konfiguruje moduł uwierzytelniania WS-Federation (WSFAM). Opcjonalna.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|Sekcja konfiguracji uwierzytelniania przy użyciu protokołu WS-Federation.|  
  
## <a name="remarks"></a>Uwagi  
 Element \<federationConfiguration > zawiera ustawienia w dwóch różnych scenariuszach:  
  
- W przypadku korzystania z protokołu WS-Federation w pasywnej aplikacji sieci Web element zawiera ustawienia, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> które konfigurują (WSFAM <xref:System.IdentityModel.Services.SessionAuthenticationModule> ) i (sam). Odwołuje się on również do konfiguracji tożsamości, która będzie używana do konfigurowania obsługi tokenów zabezpieczających i certyfikatów oraz składników, takich jak Menedżer autoryzacji oświadczeń i Menedżer uwierzytelniania oświadczeń.  
  
- W przypadku użycia <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> lub klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie element odwołuje się do konfiguracji tożsamości, która konfiguruje Menedżera autoryzacji oświadczeń i zasady, które są używane do autoryzacji swoje. Jest to prawdziwe, nawet w scenariuszach, które nie są pasywnymi scenariuszami sieci Web. na przykład aplikacje Windows Communication Foundation (WCF) lub aplikacja, która nie jest oparta na sieci Web. Jeśli aplikacja nie jest pasywną aplikacją sieci Web, `<federationConfiguration>` [ \<element składnika ClaimsAuthorizationManager >](claimsauthorizationmanager.md) (i jego elementy podrzędne, jeśli istnieją) konfiguracji tożsamości, do której odwołuje się element, są jedynymi ustawieniami stosowane. Wszystkie pozostałe są ignorowane.  
  
 Niezależnie od scenariusza środowisko uruchomieniowe ładuje domyślną konfigurację Federacji. Zachowanie jest zdefiniowane w następujący sposób:  
  
1. Jeśli nie ma żadnego `<federationConfiguration>` elementu, środowisko uruchomieniowe tworzy konfigurację Federacji i wypełnia je wartościami domyślnymi. Ta domyślna konfiguracja federacji będzie odwoływać się do domyślnej konfiguracji tożsamości.  
  
2. Jeśli jest obecny `<federationConfiguration>` pojedynczy element, jest to domyślna konfiguracja federacji bez względu na to, czy ma ona nazwę, czy nie. Jeśli jego `identityConfiguration` atrybut jest określony, przywoływana jest Konfiguracja tożsamości nazwanej; w przeciwnym razie jest przywoływana domyślna konfiguracja tożsamości.  
  
3. Jeśli istnieje nienazwany `<federationConfiguration>` element, jest to domyślna konfiguracja federacji. Jeśli jego `identityConfiguration` atrybut jest określony, przywoływana jest Konfiguracja tożsamości nazwanej; w przeciwnym razie jest przywoływana domyślna konfiguracja tożsamości.  
  
4. Jeśli istnieje wiele `<federationConfiguration>` nazwanych elementów i nie ma `<federationConfiguration>` elementu bez nazwy, zgłaszany jest wyjątek.  
  
 Zwykle zdefiniowana jest tylko jedna `<federationConfiguration>` sekcja. Ta sekcja jest domyślną konfiguracją Federacji. Można określić wiele elementów o unikatowej nazwie `<federationConfiguration>` , jednak w tym przypadku, jeśli chcesz załadować konfigurację Federacji inną niż nazwa, należy podać procedurę obsługi dla. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>zdarzenie i ustawienie <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> właściwości wewnątrz procedury obsługi <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> na obiekt zainicjowany z wartościami z odpowiedniego `<federationConfiguration>` elementu w pliku konfiguracji.  
  
 Element jest reprezentowany <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> przez klasę. `<federationConfiguration>` Sam obiekt konfiguracji jest reprezentowany przez <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> klasę. Pojedyncze <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> wystąpienie jest ustawione <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> dla właściwości i zapewnia konfigurację federacyjną dla aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XML przedstawia `<federationConfiguration>` element określający ustawienia dla WSFAM i określa, że domyślny program obsługi plików cookie (wystąpienie <xref:System.IdentityModel.Services.ChunkedCookieHandler> klasy) będzie używany przez sam.  
  
> [!WARNING]
> W tym przykładzie żadna procedura obsługi plików cookie i WSFAM nie jest wymagana do korzystania z protokołu HTTPS. Jest to spowodowane tym `requireHttps` , że atrybut `<wsFederation>` elementu `<cookieHandlerElement>` i `requireSsl` atrybutu na `false`. Te ustawienia nie są zalecane w przypadku większości środowisk produkcyjnych, ponieważ mogą one stanowić zagrożenie dla bezpieczeństwa.  
  
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
