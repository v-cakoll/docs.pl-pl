---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 0ce2e06ee895d09de193bac1fe7038e71794dda4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942542"
---
# <a name="roleclaimtype"></a>\<roleClaimType>
Określa typ oświadczenia, który definiuje oświadczenia typu roli w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiektów zwracanych <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> przez metodę procedury obsługi tokenu.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<add>  
\<samlSecurityTokenRequirement>  
\<roleClaimType>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
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
|value|Ciąg określający identyfikator URI, który reprezentuje typ zgłoszenia do użycia dla typu roli.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , klasy lub klasy pochodnej jednej z tych klas.|  
  
## <a name="remarks"></a>Uwagi  
 Element ustawia właściwość, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> gdy <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiekt jest inicjowany z konfiguracji. `<roleClaimType>`  
  
## <a name="example"></a>Przykład  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
