---
title: '&lt;federationConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9abe07c065dbea67c5ebc4a4490d9f88258130c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltfederationconfigurationgt"></a>&lt;federationConfiguration&gt;
Konfiguruje <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) za pomocą federacyjnych uwierzytelniania za pomocą protokołu WS-Federation. Konfiguruje <xref:System.Security.Claims.ClaimsAuthorizationManager> przy użyciu <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach.  
  
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
|nazwa|Nazwa tego elementu konfiguracji federacji. Ten atrybut głównie udostępnia punkt rozszerzalności dla przyszłych protokołów. Opcjonalny.|  
|identityConfigurationName|Nazwa określona w sekcji konfiguracyjnej tożsamości [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) z elementów. Jeśli ten atrybut nie jest określony, używana jest sekcji konfiguracji domyślnej tożsamości. Opcjonalny.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Umożliwia skonfigurowanie programu obsługi plików cookie używany przez Menedżera kont zabezpieczeń. Opcjonalny.|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Określa certyfikat, który jest używany do szyfrowania i odszyfrowywania tokenów. Opcjonalny.|  
|[\<wsFederation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|Konfiguruje moduł uwierzytelniania protokołu WS-Federation (WSFAM). Opcjonalny.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.identityModel.services >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|Sekcja konfiguracyjna do uwierzytelniania przy użyciu protokołu WS-Federation.|  
  
## <a name="remarks"></a>Uwagi  
 \<FederationConfiguration > element udostępnia ustawienia w dwóch scenariuszy:  
  
-   Korzystając z WS-Federation passive aplikacji sieci Web, element zawiera ustawienia służące do konfiguracji <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM). Odwołuje się również konfigurację tożsamości, aby można używać do konfigurowania, obsługi tokenu zabezpieczeń i certyfikatów i składników, takich jak Menedżer autoryzacji oświadczeń i menedżerem uwierzytelniania oświadczeń.  
  
-   Korzystając z <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie, element odwołuje się do konfiguracji tożsamości, która umożliwia skonfigurowanie programu Menedżer autoryzacji oświadczeń i zasad, które jest używane do obliczania autoryzacji decyzji. Jest to wartość true, nawet w przypadku scenariuszy, które nie są pasywnym scenariusze sieci Web; na przykład aplikacji Windows Communication Foundation (WCF) lub aplikacji, która nie jest oparte na sieci Web. Jeśli aplikacja nie jest pasywny aplikacji sieci Web, [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) — element (i jego zasady elementów podrzędnych, a jeśli istnieje) konfiguracji tożsamości odwołuje się `<federationConfiguration>` — element tylko ustawienia są stosowane. Wszystkie pozostałe są ignorowane.  
  
 Niezależnie od tego, w tym scenariuszu środowisko uruchomieniowe ładuje domyślnej konfiguracji federacji. Zachowanie jest zdefiniowane w następujący sposób:  
  
1.  W przypadku nie `<federationConfiguration>` element istnieje, tworzy konfiguracji Federacji środowiska uruchomieniowego i wypełnia wartości domyślne. Domyślna konfiguracja tożsamości będzie odwoływać się do tej domyślnej konfiguracji federacji.  
  
2.  Jeśli jeden `<federationConfiguration>` elementu, jest domyślna konfiguracja federacyjnego niezależnie od tego, czy jest nazwane i nienazwane. Jeśli jej `identityConfiguration` określony atrybut odwołuje się do konfiguracji nazwanych tożsamości; w przeciwnym razie odwołuje się do domyślnej konfiguracji tożsamości.  
  
3.  Jeśli nienazwane `<federationConfiguration>` elementu, jest domyślna konfiguracja federacyjnego. Jeśli jej `identityConfiguration` określony atrybut odwołuje się do konfiguracji nazwanych tożsamości; w przeciwnym razie odwołuje się do domyślnej konfiguracji tożsamości.  
  
4.  Jeśli wiele o nazwie `<federationConfiguration>` elementy są obecne i nie nienazwane `<federationConfiguration>` elementu, jest zgłaszany wyjątek.  
  
 Zazwyczaj tylko jeden `<federationConfiguration>` sekcja jest zdefiniowana. Ta sekcja ma domyślnej konfiguracji federacji. Można określić wiele jednoznacznie nazwane `<federationConfiguration>` elementów; jednak w tym przypadku jeśli chcesz załadować konfiguracji Federacji, innego niż ten, bez nazwy, należy podać program obsługi. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>zdarzenia i zestaw <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> właściwości wewnątrz obsługi ma <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> obiekt inicjowany z wartościami z wykorzystaniem odpowiedniej `<federationConfiguration>` w pliku konfiguracji.  
  
 `<federationConfiguration>` Reprezentowany przez element <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> klasy. Sam obiekt konfiguracji jest reprezentowana przez <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> klasy. Pojedynczy <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> wystąpienia jest ustawiona na <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> właściwości i zapewnia federacyjnych konfigurację aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono XML `<federationConfiguration>` element, który określa ustawienia dla WSFAM i określa, że plik cookie domyślny program obsługi (wystąpienie <xref:System.IdentityModel.Services.ChunkedCookieHandler> klasy) używane przez Menedżera kont zabezpieczeń.  
  
> [!WARNING]
>  W tym przykładzie obsługa plików cookie ani WSFAM są wymagane do używania protokołu HTTPS. Jest to spowodowane `requireHttps` atrybutu `<wsFederation>` elementu i `requireSsl` atrybutu `<cookieHandlerElement>` są `false`. Te ustawienia nie są zalecane dla większości środowisk produkcyjnych, ponieważ mogą one stanowić zagrożenie bezpieczeństwa.  
  
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
