---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: bcd8e00b770517e3faff011b4acee08ebdc5a0df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152739"
---
# <a name="federationconfiguration"></a>\<federationConfiguration>
Konfiguruje <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> i (SAM) podczas korzystania z uwierzytelniania federacyjnego za pośrednictwem protokołu Federacji WS. Konfiguruje <xref:System.Security.Claims.ClaimsAuthorizationManager> podczas <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> korzystania <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> z lub klasy, aby zapewnić kontrolę dostępu opartą na oświadczeniach.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
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
|name|Nazwa tego elementu konfiguracji federacji. Ten atrybut zapewnia przede wszystkim punkt rozszerzalności dla przyszłych protokołów. Element opcjonalny.|  
|nazwa tożsamościKonfiguracja|Nazwa sekcji konfiguracji tożsamości, jak określono w [ \<identityConfiguration>](identityconfiguration.md) element do użycia. Jeśli ten atrybut nie jest określony, używana jest domyślna sekcja konfiguracji tożsamości. Element opcjonalny.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>cookiehandler](cookiehandler.md)|Konfiguruje program obsługi plików cookie używany przez sam. Element opcjonalny.|  
|[\<serwisCertificate>](servicecertificate.md)|Konfiguruje certyfikat używany do szyfrowania i odszyfrowywania tokenów. Element opcjonalny.|  
|[\<wsFederation>](wsfederation.md)|Konfiguruje moduł uwierzytelniania federacji WS (WSFAM). Element opcjonalny.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|Sekcja Konfiguracji uwierzytelniania przy użyciu protokołu Federacji WS.|  
  
## <a name="remarks"></a>Uwagi  
 Element \<> konfiguracji federation zawiera ustawienia w dwóch różnych scenariuszach:  
  
- Podczas korzystania z federacji WS w pasywnej aplikacji sieci <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> Web element zawiera ustawienia, które konfigurują (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM). Odwołuje się również do konfiguracji tożsamości, która ma być używana do konfigurowania programów obsługi tokenów zabezpieczających i certyfikatów oraz składników, takich jak menedżer autoryzacji oświadczeń i menedżer uwierzytelniania oświadczeń.  
  
- Podczas korzystania <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> z <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> lub klasy do zapewnienia kontroli dostępu na podstawie oświadczeń w kodzie, element odwołuje się do konfiguracji tożsamości, która konfiguruje menedżera autoryzacji oświadczeń i zasady, które są używane do podejmowania decyzji dotyczących autoryzacji. Jest to prawdą, nawet w scenariuszach, które nie są pasywne scenariusze sieci Web; na przykład aplikacje Windows Communication Foundation (WCF) lub aplikacja, która nie jest oparta na sieci Web. Jeśli aplikacja nie jest pasywną aplikacją sieci Web, [ \<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (i jego elementy zasad podrzędnych, jeśli są obecne) konfiguracji tożsamości, do których odwołuje się `<federationConfiguration>` element, są jedynymi ustawieniami zastosowanymi. Wszystkie inne są ignorowane.  
  
 Niezależnie od scenariusza środowisko wykonawcze ładuje domyślną konfigurację federacji. Zachowanie jest zdefiniowane w następujący sposób:  
  
1. Jeśli nie `<federationConfiguration>` ma żadnego elementu, środowisko wykonawcze tworzy konfigurację federacji i wypełnia ją wartościami domyślnymi. Ta domyślna konfiguracja federacji odwołuje się do domyślnej konfiguracji tożsamości.  
  
2. Jeśli pojedynczy `<federationConfiguration>` element jest obecny, jest to domyślna konfiguracja federacji, niezależnie od tego, czy jest nazwany lub nienazwany. Jeśli `identityConfiguration` jego atrybut jest określony, odwołuje się do nazwanej konfiguracji tożsamości; w przeciwnym razie odwołuje się do domyślnej konfiguracji tożsamości.  
  
3. Jeśli element `<federationConfiguration>` bez nazwy jest obecny, jest to domyślna konfiguracja federacji. Jeśli `identityConfiguration` jego atrybut jest określony, odwołuje się do nazwanej konfiguracji tożsamości; w przeciwnym razie odwołuje się do domyślnej konfiguracji tożsamości.  
  
4. Jeśli wiele `<federationConfiguration>` nazwanych elementów `<federationConfiguration>` są obecne i nie ma elementu bez nazwy, wyjątek.  
  
 Zazwyczaj zdefiniowano tylko `<federationConfiguration>` jedną sekcję. Ta sekcja jest domyślną konfiguracją federacji. Można określić wiele elementów `<federationConfiguration>` o unikatowej nazwie; jednak w tym przypadku, jeśli chcesz załadować konfigurację federacji inne niż bez nazwy, należy podać program obsługi dla. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>i ustawić <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> właściwość wewnątrz programu <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> obsługi do obiektu zainicjowanego z wartościami z odpowiedniego `<federationConfiguration>` elementu w pliku konfiguracyjnym.  
  
 Element `<federationConfiguration>` jest reprezentowany <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> przez klasę. Sam obiekt konfiguracji jest reprezentowany przez <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> klasę. Pojedyncze <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> wystąpienie jest <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> ustawiona na właściwości i zapewnia konfigurację federacyjne dla aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XML przedstawia `<federationConfiguration>` element, który określa ustawienia dla WSFAM i określa, <xref:System.IdentityModel.Services.ChunkedCookieHandler> że domyślny program obsługi plików cookie (wystąpienie klasy) będzie używany przez SAM.  
  
> [!WARNING]
> W tym przykładzie ani obsługi plików cookie ani WSFAM są wymagane do korzystania z protokołu HTTPS. Dzieje `requireHttps` się tak, ponieważ `<wsFederation>` atrybut `requireSsl` elementu i `<cookieHandlerElement>` atrybut `false`na są . Te ustawienia nie są zalecane w większości środowisk produkcyjnych, ponieważ mogą one stanowić zagrożenie bezpieczeństwa.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<>konfiguracji tożsamości](identityconfiguration.md)
