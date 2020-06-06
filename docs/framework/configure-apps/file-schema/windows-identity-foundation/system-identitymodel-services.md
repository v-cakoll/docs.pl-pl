---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152507"
---
# \<system.identityModel.services>
Sekcja konfiguracji uwierzytelniania przy użyciu protokołu WS-Federation.  
  
[**\<configuration>**](../configuration-element.md)\
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
|[\<federationConfiguration>](federationconfiguration.md)|Zawiera ustawienia służące do konfigurowania <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> modułów HTTP (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (sam).|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
 Brak  
  
## <a name="remarks"></a>Uwagi  
 Dodaj `<system.identityModel.services>` sekcję do pliku konfiguracji aplikacji, aby podać ustawienia dla sam i WSFAM.  
  
> [!IMPORTANT]
> Przy użyciu <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub klasy w <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie, Menedżer autoryzacji oświadczeń ( <xref:System.Security.Claims.ClaimsAuthorizationManager> ) i zasady, które są używane do podejmowania decyzji dotyczących autoryzacji, są konfigurowane za pośrednictwem `<identityConfiguration>` elementu, który jest niejawnie lub jawnie przywoływany z `<federationConfiguration>` elementu w tej sekcji. Aby uzyskać więcej informacji, zobacz **uwagi** w obszarze [\<federationConfiguration>](federationconfiguration.md) elementu.  
  
 `<system.identityModel.services>`Sekcja jest reprezentowana przez <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> klasę. Kolekcja `<federationConfiguration>` elementów podrzędnych skonfigurowanych w sekcji jest reprezentowana przez <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> klasę.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XML pokazuje, jak dodać `<system.identityModel.services>` sekcję do pliku konfiguracji. Należy najpierw dodać deklaracje sekcji dla `<system.identityModel.services>` sekcji i części `<system.identityModel>` . (Po dodaniu `<system.identityModel.services>` sekcji należy również dodać deklarację dla `<system.identityModel>` sekcji, aby upewnić się, że w `<identityConfiguration>` razie potrzeby środowisko uruchomieniowe może utworzyć domyślną sekcję). Po dodaniu deklaracji sekcji można skonfigurować ustawienia uwierzytelniania federacyjnego w obszarze `<system.identityModel.services>` elementu.  
  
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
