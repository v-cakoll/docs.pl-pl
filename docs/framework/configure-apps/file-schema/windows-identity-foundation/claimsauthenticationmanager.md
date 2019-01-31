---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: ecf26263bf47e8b4609e7adc208f0a59a2fa795b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255188"
---
# <a name="claimsauthenticationmanager"></a>\<claimsAuthenticationManager>
Rejestruje Menedżera uwierzytelniania oświadczeń dla oświadczeń przychodzących.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<claimsAuthenticationManager>  
  
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
|— typ|Określa typ niestandardowy, który pochodzi od klasy <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy. Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do niestandardowego typu].|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 W przypadku nie `type` atrybut, lub jeśli `type` atrybutu odwołania <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy `<claimsAuthenticationManager>` element nie ma elementów podrzędnych; jednak klasy pochodne klasy <xref:System.Security.Claims.ClaimsAuthenticationManager> można zdefiniować podrzędne elementy konfiguracji.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Określa ustawienia tożsamości na poziomie usługi.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślne zachowanie, dostępne za pośrednictwem <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy funkcją oświadczeń przychodzących. Jeśli nie `type` atrybut jest określony lub jeśli `type` Określa atrybut <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy `<claimsAuthenticationManager>` element nie ma elementów podrzędnych. Można określić `type` pochodną klasy atrybutu, aby zarejestrować typ <xref:System.Security.Claims.ClaimsAuthenticationManager> klasę, aby wdrożyć niestandardowe zachowanie. Klasy pochodne mogą obsługiwać konfiguracji za pomocą elementów podrzędnych `<claimsAuthenticationManager>` elementu przez zastąpienie <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metodę obsługującą te elementy. Projektant klasy zależy od schematu zdefiniowane dla elementów podrzędnych.  
  
 `<claimsAuthenticationManager>` Ustawia element <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="example"></a>Przykład  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
