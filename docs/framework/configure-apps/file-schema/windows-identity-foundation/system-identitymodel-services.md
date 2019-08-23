---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: bef061c5c982fb0e740f889336a3b334bc19225e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943656"
---
# <a name="systemidentitymodelservices"></a>\<system.identityModel.services>
Sekcja konfiguracji uwierzytelniania przy użyciu protokołu WS-Federation.  
  
 \<system.identityModel.services>  
  
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
|[\<federationConfiguration>](federationconfiguration.md)|Zawiera ustawienia służące do <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> konfigurowania modułów HTTP (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> i (sam).|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
 Brak  
  
## <a name="remarks"></a>Uwagi  
 `<system.identityModel.services>` Dodaj sekcję do pliku konfiguracji aplikacji, aby podać ustawienia dla sam i WSFAM.  
  
> [!IMPORTANT]
> Przy użyciu <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.Security.Claims.ClaimsAuthorizationManager>lub klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie, Menedżer autoryzacji oświadczeń () i zasady służące `<identityConfiguration>` do podejmowania decyzji dotyczących autoryzacji są konfigurowane za pośrednictwem <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> element, który jest niejawnie lub jawnie przywoływany z `<federationConfiguration>` elementu w tej sekcji. Aby uzyskać więcej informacji, zobacz **uwagi** poniżej [ \<elementu federationConfiguration >](federationconfiguration.md) .  
  
 Sekcja jest reprezentowana <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> przez klasę. `<system.identityModel.services>` Kolekcja elementów podrzędnych `<federationConfiguration>` skonfigurowanych w sekcji jest reprezentowana <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> przez klasę.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XML pokazuje, `<system.identityModel.services>` jak dodać sekcję do pliku konfiguracji. Należy najpierw dodać deklaracje sekcji dla `<system.identityModel.services>` sekcji `<system.identityModel>` i części. (Po dodaniu `<system.identityModel.services>` sekcji należy również dodać deklarację `<system.identityModel>` dla sekcji, aby upewnić się, że w razie `<identityConfiguration>` potrzeby środowisko uruchomieniowe może utworzyć domyślną sekcję). Po dodaniu deklaracji sekcji można skonfigurować ustawienia uwierzytelniania federacyjnego w obszarze `<system.identityModel.services>` elementu.  
  
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
