---
title: '&lt;nameClaimType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2c53886458b4c6e2867e1f9fddd4ab50b199c660
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltnameclaimtypegt"></a>&lt;nameClaimType&gt;
Ustawia typ oświadczenia, która określa <xref:System.Security.Principal.IIdentity.Name%2A> właściwości. Typ oświadczenia jest używana do wyszukania <xref:System.Security.Claims.Claim> w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiekty zwrócone przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metoda tego programu obsługi tokenów. Następnie ustawionej wartości zgodne oświadczenie jako nazwa <xref:System.Security.Principal.IIdentity> generowane na podstawie tego programu obsługi tokenów.  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<Dodaj >  
\<samlSecurityTokenRequirement >  
\<nameClaimType >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|value|Ciąg określający URI, który reprezentuje typ oświadczenia oświadczenia do użycia na potrzeby <xref:System.Security.Principal.IIdentity.Name%2A> właściwości. Wymagany.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej każdej z tych klas.|  
  
## <a name="remarks"></a>Uwagi  
 `<nameClaimType>` Ustawia element <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> właściwości podczas <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiekt został zainicjowany z konfiguracji.  
  
## <a name="example"></a>Przykład  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
