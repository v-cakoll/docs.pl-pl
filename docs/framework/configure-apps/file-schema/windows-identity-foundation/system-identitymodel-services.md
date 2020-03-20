---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152507"
---
# <a name="systemidentitymodelservices"></a>\<system.identityModel.services>
Sekcja Konfiguracji uwierzytelniania przy użyciu protokołu Federacji WS.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
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
 Brak  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Zawiera ustawienia, które <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> konfigurują moduły HTTP <xref:System.IdentityModel.Services.SessionAuthenticationModule> (WSFAM) i (SAM).|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
 Brak  
  
## <a name="remarks"></a>Uwagi  
 Dodaj `<system.identityModel.services>` sekcję do pliku konfiguracyjnego aplikacji, aby zapewnić ustawienia dla SAM i WSFAM.  
  
> [!IMPORTANT]
> Podczas korzystania <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> z <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> lub klasy do zapewnienia kontroli dostępu na podstawie<xref:System.Security.Claims.ClaimsAuthorizationManager>oświadczeń w kodzie, menedżer autoryzacji oświadczeń ( `<identityConfiguration>` ) i zasady, które jest `<federationConfiguration>` używany do podejmowania decyzji autoryzacji są konfigurowane za pośrednictwem elementu, który jest niejawnie lub jawnie odwołuje się z elementu w tej sekcji. Aby uzyskać więcej informacji, zobacz **Uwagi** w [ \<obszarze federationConfiguration>](federationconfiguration.md) element.  
  
 Sekcja `<system.identityModel.services>` jest reprezentowana <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> przez klasę. Kolekcja elementów `<federationConfiguration>` podrzędnych skonfigurowanych w sekcji <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> jest reprezentowana przez klasę.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XML pokazuje, jak dodać sekcję `<system.identityModel.services>` do pliku konfiguracyjnego. Należy najpierw dodać deklaracje sekcji `<system.identityModel.services>` zarówno `<system.identityModel>` dla sekcji, jak i sekcji. (Podczas dodawania `<system.identityModel.services>` sekcji należy również dodać deklarację dla `<system.identityModel>` sekcji, `<identityConfiguration>` aby upewnić się, że domyślna sekcja może zostać utworzona przez środowisko wykonawcze, jeśli to konieczne). Po dodaniu deklaracji sekcji można skonfigurować ustawienia uwierzytelniania federacyjnego w `<system.identityModel.services>` ramach elementu.  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
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
  
</configuration>  
```
