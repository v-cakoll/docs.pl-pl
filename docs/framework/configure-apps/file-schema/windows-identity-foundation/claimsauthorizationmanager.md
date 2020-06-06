---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: ddbe8a862940272e4192a3f4c0abdc1f9e8b5d48
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252086"
---
# \<claimsAuthorizationManager>
Rejestruje Menedżera autoryzacji oświadczeń dla oświadczeń przychodzących.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthorizationManager>**  
  
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
|typ|Typ niestandardowy, który pochodzi od <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy. Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych](../windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Jeśli nie ma `type` atrybutu lub jeśli `type` atrybut odwołuje się do <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy, element nie `<claimsAuthorizationManager>` przyjmuje elementów podrzędnych, jednak klasy pochodne <xref:System.Security.Claims.ClaimsAuthorizationManager> mogą definiować podrzędne elementy konfiguracji.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Określa ustawienia tożsamości na poziomie usług.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślne zachowanie udostępniane przez <xref:System.Security.Claims.ClaimsAuthorizationManager> klasę zawsze autoryzuje oświadczenia przychodzące. Jeśli nie `type` określono atrybutu lub jeśli `type` atrybut określa <xref:System.Security.Claims.ClaimsAuthorizationManager> klasę, `<claimsAuthorizationManager>` element nie przyjmuje elementów podrzędnych. Możesz określić atrybut, `type` Aby zarejestrować typ pochodny <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy, aby zaimplementować zachowanie niestandardowe. Klasy pochodne mogą obsługiwać konfigurację za pomocą elementów podrzędnych `<claimsAuthorizationManager>` elementu przez zastąpienie <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> metody do obsługi tych elementów. Schemat zdefiniowany dla elementów podrzędnych jest projektantem klasy.  
  
> [!IMPORTANT]
> W przypadku użycia <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie Konfiguracja tożsamości, do której odwołuje się `<federationConfiguration>` element, konfiguruje Menedżera autoryzacji oświadczeń i zasady, które są używane w celu podejmowania decyzji dotyczących autoryzacji. Dotyczy to nawet scenariuszy, które nie są pasywnymi scenariuszami sieci Web, na przykład aplikacji Windows Communication Foundation (WCF) lub aplikacji, które nie są oparte na sieci Web. Jeśli aplikacja nie jest pasywną aplikacją sieci Web, `<claimsAuthorizationManager>` element (i jego elementy zasad podrzędnych, jeśli istnieją) przywoływanej konfiguracji tożsamości są jedynymi stosowanymi ustawieniami. Wszystkie inne ustawienia są ignorowane. Aby uzyskać więcej informacji, zobacz [\<federationConfiguration>](federationconfiguration.md) element.  
  
 Ten element ustawia <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> Właściwość.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie XML przedstawiono konfigurację Menedżera autoryzacji oświadczeń, który implementuje zasady składające się z par akcji zasobów, z których każda określa logiczne kombinacje oświadczeń, które obiekt żądający musi dysponować, aby wykonać akcję dla zasobu. Kod implementujący Menedżera autoryzacji oświadczeń, który może korzystać z tych zasad, można znaleźć w `ClaimsBasedAuthorization` przykładzie.  
  
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
