---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: 74ca031f7017d51adaa7a71593f537b64abbeae6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942890"
---
# <a name="claimsauthorizationmanager"></a>\<Składnika ClaimsAuthorizationManager >
Rejestruje Menedżera autoryzacji oświadczeń dla oświadczeń przychodzących.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<Składnika ClaimsAuthorizationManager >  
  
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
|— typ|Typ niestandardowy, który pochodzi od <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy. Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych](../windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Jeśli `type` nie ma atrybutu lub <xref:System.Security.Claims.ClaimsAuthenticationManager> `type` Jeśli atrybut `<claimsAuthorizationManager>` odwołuje się do klasy, element nie przyjmuje elementów podrzędnych, jednak klasy pochodne <xref:System.Security.Claims.ClaimsAuthorizationManager> mogą definiować podrzędne elementy konfiguracji.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Określa ustawienia tożsamości na poziomie usług.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślne zachowanie udostępniane przez <xref:System.Security.Claims.ClaimsAuthorizationManager> klasę zawsze autoryzuje oświadczenia przychodzące. Jeśli nie `type` określono atrybutu lub `type` Jeśli atrybut `<claimsAuthorizationManager>` określa <xref:System.Security.Claims.ClaimsAuthorizationManager> klasę, element nie przyjmuje elementów podrzędnych. Możesz określić atrybut, `type` aby zarejestrować typ pochodny klasy, <xref:System.Security.Claims.ClaimsAuthorizationManager> aby zaimplementować zachowanie niestandardowe. Klasy pochodne mogą obsługiwać konfigurację za pomocą elementów `<claimsAuthorizationManager>` podrzędnych elementu przez <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> zastąpienie metody do obsługi tych elementów. Schemat zdefiniowany dla elementów podrzędnych jest projektantem klasy.  
  
> [!IMPORTANT]
> W przypadku użycia <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> lub klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie Konfiguracja tożsamości `<federationConfiguration>` , do której odwołuje się element, konfiguruje Menedżera autoryzacji oświadczeń i zasady, które są używane do wykonania decyzje dotyczące autoryzacji. Dotyczy to nawet scenariuszy, które nie są pasywnymi scenariuszami sieci Web, na przykład aplikacji Windows Communication Foundation (WCF) lub aplikacji, które nie są oparte na sieci Web. Jeśli aplikacja nie jest pasywną aplikacją sieci Web, `<claimsAuthorizationManager>` element (i jego elementy zasad podrzędnych, jeśli istnieją) przywoływanej konfiguracji tożsamości są jedynymi stosowanymi ustawieniami. Wszystkie inne ustawienia są ignorowane. Aby uzyskać więcej informacji, zobacz [ \<federationConfiguration >](federationconfiguration.md) elementu.  
  
 Ten element ustawia <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> właściwość.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie XML przedstawiono konfigurację Menedżera autoryzacji oświadczeń, który implementuje zasady składające się z par akcji zasobów, z których każda określa logiczne kombinacje oświadczeń, które obiekt żądający musi dysponować, aby wykonać akcję dla zasobu. Kod implementujący Menedżera autoryzacji oświadczeń, który może korzystać z tych zasad, `ClaimsBasedAuthorization` można znaleźć w przykładzie.  
  
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
