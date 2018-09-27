---
title: '&lt;federationConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: 66fa16992d779b08ee8c55598efc98f8f5267656
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399208"
---
# <a name="ltfederationconfigurationgt"></a>&lt;federationConfiguration&gt;
Konfiguruje <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) za pomocą federacyjnego uwierzytelniania za pomocą protokołu WS-Federation. Konfiguruje <xref:System.Security.Claims.ClaimsAuthorizationManager> przy użyciu <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach.  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
  
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
|nazwa|Nazwa tego elementu konfiguracji federacji. Ten atrybut przede wszystkim udostępnia punkt rozszerzalności dla przyszłych protokołów. Opcjonalna.|  
|identityConfigurationName|Nazwa sekcji konfiguracji tożsamości, jak to określono w [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu do użycia. Jeśli ten atrybut nie jest określony, sekcja konfiguracji domyślnej tożsamości jest używana. Opcjonalna.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Konfiguruje używane przez SAM program obsługi plików cookie. Opcjonalna.|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Umożliwia skonfigurowanie certyfikatu, który jest używany do szyfrowania i odszyfrowywania tokenów. Opcjonalna.|  
|[\<wsFederation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|Konfiguruje moduł uwierzytelniania protokołu WS-Federation (WSFAM). Opcjonalna.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.identityModel.services >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|Sekcja konfiguracji uwierzytelniania przy użyciu protokołu WS-Federation.|  
  
## <a name="remarks"></a>Uwagi  
 \<FederationConfiguration > element zawiera ustawienia w dwóch różnych scenariuszach:  
  
-   Korzystając z WS-Federation passive aplikacji sieci Web, element zawiera ustawienia służące do konfiguracji <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM). Odwołuje się również konfiguracja tożsamości, które ma być używany do konfigurowania programy obsługi tokenów zabezpieczających i certyfikaty i składników, takich jak Menedżer autoryzacji oświadczeń i oświadczenia Menedżera uwierzytelniania.  
  
-   Korzystając z <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie, element odwołuje się do konfiguracji tożsamości, która umożliwia skonfigurowanie programu Menedżer autoryzacji oświadczeń i zasady, które jest używane do utworzenia autoryzacji decyzje. Ta zasada obowiązuje, nawet w scenariuszach, które nie są pasywnym scenariusze sieci Web; na przykład aplikacji Windows Communication Foundation (WCF) lub aplikacji, która nie jest oparte na sieci Web. Jeśli aplikacja nie jest pasywnym aplikacji sieci Web, [ \<składnika claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) — element (i jego zasady elementów podrzędnych, a jeśli jest obecna) konfiguracji tożsamości odwołuje się `<federationConfiguration>` — element tylko ustawienia są stosowane. Wszystkie pozostałe są ignorowane.  
  
 Niezależnie od tego, w tym scenariuszu środowisko uruchomieniowe ładuje domyślnej konfiguracji federacji. To zachowanie jest zdefiniowana w następujący sposób:  
  
1.  Jeśli ma nie `<federationConfiguration>` element jest obecny, środowisko uruchomieniowe umożliwia utworzenie konfiguracji Federacji i wypełnia ją wartościami domyślnymi. Tej domyślnej konfiguracji Federacji będzie odwoływać się domyślnej konfiguracji tożsamości.  
  
2.  Jeśli jeden `<federationConfiguration>` element jest obecny, jest domyślna konfiguracja Federacji, niezależnie od tego, czy jest nazwane i nienazwane. Jeśli jej `identityConfiguration` atrybut jest określony, odwołuje się do konfiguracji o nazwie tożsamości; w przeciwnym razie odwołuje się do domyślnej konfiguracji tożsamości.  
  
3.  Jeśli nienazwane `<federationConfiguration>` element jest obecny, jest domyślna konfiguracja federacji. Jeśli jej `identityConfiguration` atrybut jest określony, odwołuje się do konfiguracji o nazwie tożsamości; w przeciwnym razie odwołuje się do domyślnej konfiguracji tożsamości.  
  
4.  Jeśli nazwany wielu `<federationConfiguration>` elementy są dostępne i nie nienazwane `<federationConfiguration>` element jest obecny, zgłaszany jest wyjątek.  
  
 Zwykle, tylko jeden `<federationConfiguration>` sekcja jest zdefiniowana. Ta sekcja jest domyślna konfiguracja federacji. Można określić wiele, unikatową nazwę `<federationConfiguration>` elementów; jednak w tym przypadku jeśli chcesz załadować konfiguracji Federacji, innym niż bez nazwy, musisz podać program obsługi. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> zdarzenia i ustaw <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> właściwości wewnątrz procedury obsługi do <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> obiekt został zainicjowany przy użyciu wartości z odpowiedniego `<federationConfiguration>` elementu w pliku konfiguracji.  
  
 `<federationConfiguration>` Element jest reprezentowany przez <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> klasy. Sam obiekt konfiguracji jest reprezentowany przez <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> klasy. Pojedynczy <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> wystąpienia jest ustawiona na <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> właściwości i zapewnia federacyjnego konfiguracji dla aplikacji.  
  
## <a name="example"></a>Przykład  
 Pokazano w poniższym XML `<federationConfiguration>` element, który określa ustawienia dla WSFAM i określa, że domyślny program obsługi plików cookie (wystąpienie <xref:System.IdentityModel.Services.ChunkedCookieHandler> klasy) używane przez Menedżera kont zabezpieczeń.  
  
> [!WARNING]
>  W tym przykładzie program obsługi plików cookie ani WSFAM są wymagane do używania protokołu HTTPS. Jest to spowodowane `requireHttps` atrybutu na `<wsFederation>` elementu i `requireSsl` atrybutu na `<cookieHandlerElement>` są `false`. Te ustawienia nie są zalecane dla większości środowisk produkcyjnych, ponieważ mogą one stwarzać zagrożenie bezpieczeństwa.  
  
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
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>  
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>  
 [\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)
