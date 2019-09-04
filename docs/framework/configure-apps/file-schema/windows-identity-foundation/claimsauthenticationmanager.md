---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: c901daf4d442a206345301795c7a4bdc076329cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252088"
---
# <a name="claimsauthenticationmanager"></a>\<claimsAuthenticationManager>
Rejestruje Menedżera uwierzytelniania oświadczeń dla oświadczeń przychodzących.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimsAuthenticationManager >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|— typ|Określa typ niestandardowy, który pochodzi od <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy. Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych].|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Jeśli `type` nie ma atrybutu lub <xref:System.Security.Claims.ClaimsAuthenticationManager> `type` Jeśli atrybut `<claimsAuthenticationManager>` odwołuje się do klasy, element nie przyjmuje elementów podrzędnych, jednak klasy pochodne <xref:System.Security.Claims.ClaimsAuthenticationManager> mogą definiować podrzędne elementy konfiguracji.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Określa ustawienia tożsamości na poziomie usług.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślne zachowanie udostępniane przez <xref:System.Security.Claims.ClaimsAuthenticationManager> klasę zwraca oświadczenia przychodzące. Jeśli nie `type` określono atrybutu lub `type` Jeśli atrybut `<claimsAuthenticationManager>` określa <xref:System.Security.Claims.ClaimsAuthenticationManager> klasę, element nie przyjmuje elementów podrzędnych. Możesz określić atrybut, `type` aby zarejestrować typ pochodny klasy, <xref:System.Security.Claims.ClaimsAuthenticationManager> aby zaimplementować zachowanie niestandardowe. Klasy pochodne mogą obsługiwać konfigurację za pomocą elementów `<claimsAuthenticationManager>` podrzędnych elementu przez <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> zastąpienie metody do obsługi tych elementów. Schemat zdefiniowany dla elementów podrzędnych jest projektantem klasy.  
  
 `<claimsAuthenticationManager>` Element<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> ustawia właściwość.  
  
## <a name="example"></a>Przykład  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
