---
title: '&lt;system.identityModel.services&gt;'
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: c7261d20ae2379ad33679cadecdef484f2afdecf
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778084"
---
# <a name="ltsystemidentitymodelservicesgt"></a>&lt;system.identityModel.services&gt;
Sekcja konfiguracji uwierzytelniania przy użyciu protokołu WS-Federation.  
  
 \<system.identityModel.services >  
  
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
|[\<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Zawiera ustawienia, które skonfigurować <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> moduły HTTP (SAM).|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
 Brak  
  
## <a name="remarks"></a>Uwagi  
 Dodaj `<system.identityModel.services>` sekcję do pliku konfiguracji aplikacji, aby określić ustawienia SAM i WSFAM.  
  
> [!IMPORTANT]
>  Korzystając z <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach, w kodzie, Menedżer autoryzacji oświadczeń (<xref:System.Security.Claims.ClaimsAuthorizationManager>) i zasad, który służy do podejmowania decyzji dotyczących autoryzacji są konfigurowane za pośrednictwem `<identityConfiguration>` element, który jest niejawnie lub jawnie odwoływać się z `<federationConfiguration>` elementu w tej sekcji. Aby uzyskać więcej informacji, zobacz **uwagi** w obszarze [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.  
  
 `<system.identityModel.services>` Sekcji jest reprezentowany przez <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> klasy. Kolekcja podrzędnych `<federationConfiguration>` elementów skonfigurowanych w sekcji jest reprezentowany przez <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> klasy.  
  
## <a name="example"></a>Przykład  
 Następujący kody XML pokazuje sposób dodawania `<system.identityModel.services>` sekcję do pliku konfiguracji. Należy najpierw dodać deklaracje sekcji dla obu `<system.identityModel.services>` sekcji i `<system.identityModel>` sekcje. (Po dodaniu `<system.identityModel.services>` sekcji, należy również dodać deklarację dla `<system.identityModel>` sekcji, aby upewnić się, że domyślny `<identityConfiguration>` sekcji mogą być tworzone przez środowisko wykonawcze, jeśli to konieczne.) Po dodaniu deklaracje sekcji można skonfigurować ustawienia uwierzytelniania federacyjnego w ramach `<system.identityModel.services>` elementu.  
  
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
