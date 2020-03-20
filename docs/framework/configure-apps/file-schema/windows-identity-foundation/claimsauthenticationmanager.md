---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152752"
---
# <a name="claimsauthenticationmanager"></a>\<claimsAuthenticationManager>
Rejestruje menedżera uwierzytelniania oświadczeń dla oświadczeń przychodzących.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
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
|type|Określa typ niestandardowy, który <xref:System.Security.Claims.ClaimsAuthenticationManager> pochodzi z klasy. Aby uzyskać więcej informacji `type` na temat określania atrybutu, zobacz [Odwołania do typów niestandardowych].|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Jeśli nie `type` ma żadnego atrybutu `type` lub jeśli <xref:System.Security.Claims.ClaimsAuthenticationManager> atrybut `<claimsAuthenticationManager>` odwołuje się do klasy, element nie przyjmuje elementów podrzędnych; jednak klasy uzyskane <xref:System.Security.Claims.ClaimsAuthenticationManager> z można zdefiniować elementy konfiguracji podrzędnej.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>konfiguracji tożsamości](identityconfiguration.md)|Określa ustawienia tożsamości na poziomie usługi.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślne zachowanie dostarczone <xref:System.Security.Claims.ClaimsAuthenticationManager> za pośrednictwem klasy odzwierciedla oświadczenia przychodzące. Jeśli `type` nie atrybut jest określony `type` lub jeśli <xref:System.Security.Claims.ClaimsAuthenticationManager> atrybut określa `<claimsAuthenticationManager>` klasę, element nie przyjmuje elementów podrzędnych. Można określić `type` atrybut, aby zarejestrować typ <xref:System.Security.Claims.ClaimsAuthenticationManager> pochodzący z klasy, aby zaimplementować zachowanie niestandardowe. Klasy pochodne mogą obsługiwać konfigurację za pośrednictwem elementów podrzędnych `<claimsAuthenticationManager>` elementu, zastępując <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metodę obsługi tych elementów. Schemat zdefiniowany dla elementów podrzędnych jest do projektanta klasy.  
  
 Element `<claimsAuthenticationManager>` ustawia <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> właściwość.  
  
## <a name="example"></a>Przykład  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
