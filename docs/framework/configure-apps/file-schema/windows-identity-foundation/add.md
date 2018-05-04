---
title: '&lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6ee6403fcfe741d3e38bf44eddb1cf52cf856ec8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt"></a>&lt;add&gt;
Dodaje określony zabezpieczenia programu obsługi tokenów do kolekcji programu obsługi tokenów.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
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
|— typ|Nazwa typu CLR programu obsługi tokenów do dodania. Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołuje się do niestandardowego typu](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej każdej z tych klas.|  
|[\<sessionTokenRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy lub klas pochodnych.|  
|[\<userNameSecurityTokenHandlerRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|Zapewnia konfigurację <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> klasy lub klas pochodnych.|  
|[\<x509SecurityTokenHandlerRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|Zapewnia opcjonalne konfigurację <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> klasy lub klas pochodnych.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Określa kolekcję programów obsługi tokenu zabezpieczeń, które są zarejestrowane z punktem końcowym.|  
  
## <a name="remarks"></a>Uwagi  
 `<add>` Elementu można podjąć element pojedynczy element potomny, który określa konfigurację programu obsługi tokenów. Jest to zależne od tego, czy klasa obsługi, do których odwołuje się za pośrednictwem `type` atrybutu `<add>` element zapewnia obsługę dla tej funkcji. Klasy programu obsługi tokenów, które zapewniają ta funkcja musi ujawniać Konstruktor, który pobiera <xref:System.Xml.XmlElement> obiektu.  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Kilka klas programu obsługi tokenów zabezpieczeń zapewnienia tej funkcji. Te klasy są <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, i <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.  
  
> [!IMPORTANT]
>  Kolekcja programu obsługi tokenów może zawierać tylko jeden program obsługi każdego typu. Oznacza to, na przykład, że jeśli chcesz dodać obsługi, która jest pochodną <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy do kolekcji, należy najpierw usunąć <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, który ma domyślnie z kolekcji. Można użyć [ \<Usuń >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) elementu do usunięcia z kolekcji lub użyj pojedynczego obsługi [ \<Wyczyść >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) elementu do usunięcia wszystkich programów obsługi z kolekcji.  
  
 Ustawienia określone na program obsługi zastąpić równoważnym ustawień określonych w kolekcji programu obsługi tokenów [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu i określone na poziomie usługi w obszarze [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.  
  
## <a name="example"></a>Przykład  
 Następujący kod XML pokazano sposób użycia `<add>` i `<remove>` elementy, aby zastąpić domyślny sesji programu obsługi tokenów niestandardową sesję programu obsługi tokenów. Kod XML jest pobierana z `ClaimsAwareWebFarm` próbki.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
