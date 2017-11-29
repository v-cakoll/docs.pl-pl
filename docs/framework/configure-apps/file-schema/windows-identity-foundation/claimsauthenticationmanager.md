---
title: '&lt;claimsAuthenticationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 48e5be23b196a24a9d3e2a1dc4639d8ca9823660
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimsauthenticationmanagergt"></a>&lt;claimsAuthenticationManager&gt;
Rejestruje Menedżer uwierzytelniania oświadczeń oświadczeń przychodzących.  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<claimsAuthenticationManager >  
  
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
|— typ|Określa typ niestandardowy, która jest pochodną <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy. Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołania do typu niestandardowego].|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 W przypadku nie `type` atrybutu, lub jeśli `type` atrybut odwołania <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy `<claimsAuthenticationManager>` element nie ma elementów podrzędnych; jednak klasy wyprowadzone z <xref:System.Security.Claims.ClaimsAuthenticationManager> można zdefiniować podrzędne elementy konfiguracji.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Określa ustawienia tożsamości poziomu usług.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślne zachowanie realizowane za pośrednictwem <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy echa oświadczenia przychodzące. Jeśli nie `type` jest określony atrybut lub, jeśli `type` Określa atrybut <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy `<claimsAuthenticationManager>` element nie ma elementów podrzędnych. Można określić `type` atrybut, aby zarejestrować typ pochodny <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy do zaimplementowania niestandardowego zachowania. Klasy pochodne mogą obsługiwać konfiguracji za pomocą elementy podrzędne `<claimsAuthenticationManager>` elementu przez zastąpienie <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metody do obsługi tych elementów. Projektant klasy zależy od schematu zdefiniowane dla elementów podrzędnych.  
  
 `<claimsAuthenticationManager>` Ustawia element <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="example"></a>Przykład  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
