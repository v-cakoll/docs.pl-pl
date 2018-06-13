---
title: '&lt;claimsAuthorizationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 06824e20286f8905ad3a8ac9d2b4a30366a6ec10
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757375"
---
# <a name="ltclaimsauthorizationmanagergt"></a>&lt;claimsAuthorizationManager&gt;
Rejestruje Menedżera autoryzacji oświadczeń dla oświadczeń przychodzących.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<claimsAuthorizationManager >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|— typ|Typ niestandardowy, która jest pochodną <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy. Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołuje się do niestandardowego typu](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 W przypadku nie `type` atrybutu, lub jeśli `type` atrybut odwołania <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy `<claimsAuthorizationManager>` element nie ma elementów podrzędnych; jednak klasy wyprowadzone z <xref:System.Security.Claims.ClaimsAuthorizationManager> można zdefiniować podrzędne elementy konfiguracji.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Określa ustawienia tożsamości poziomu usług.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślne zachowanie realizowane za pośrednictwem <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy zawsze autoryzuje oświadczenia przychodzące. Jeśli nie `type` jest określony atrybut lub, jeśli `type` Określa atrybut <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy `<claimsAuthorizationManager>` element nie ma elementów podrzędnych. Można określić `type` atrybut, aby zarejestrować typ pochodny <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy do zaimplementowania niestandardowego zachowania. Klasy pochodne mogą obsługiwać konfiguracji za pomocą elementy podrzędne `<claimsAuthorizationManager>` elementu przez zastąpienie <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> metody do obsługi tych elementów. Projektant klasy zależy od schematu zdefiniowane dla elementów podrzędnych.  
  
> [!IMPORTANT]
>  Korzystając z <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie, konfiguracja tożsamości, który odwołuje się do niego `<federationConfiguration>` element konfiguruje Menedżera autoryzacji oświadczeń i zasad, które jest używane do obliczania decyzji dotyczących autoryzacji. Dotyczy to przypadków, nawet w przypadku scenariuszy, które nie są pasywnym scenariusze sieci Web, na przykład aplikacji Windows Communication Foundation (WCF) lub aplikacji, która nie jest oparte na sieci Web. Jeśli aplikacja nie jest pasywny aplikacji sieci Web, `<claimsAuthorizationManager>` — element (i jego zasady elementów podrzędnych, a jeśli istnieje) konfiguracji przywoływanego tożsamości są tylko ustawienia zastosowane. Wszystkie inne ustawienia są ignorowane. Aby uzyskać więcej informacji, zobacz [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.  
  
 Ten element ustawia <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="example"></a>Przykład  
 Następujący kod XML przedstawia konfigurację do autoryzacji oświadczeń manager, który implementuje zasad składa się z pary Akcja zasobu, z których każdy określa logiczna kombinacje oświadczeń, których obiekt żądający musi posiadać można wykonać akcji dla zasobu. Kod, który implementuje Menedżera autoryzacji oświadczeń możliwość korzystania z tych zasad można znaleźć w `ClaimsBasedAuthorization` próbki.  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
