---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 83ba51cbbd5100bf7412f9914a270cac88f7faa1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973801"
---
# <a name="add"></a>\<Dodaj >
Dodaje określony program obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<system. identityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**SecurityTokenHandler**](securitytokenhandlers.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dodaj >**  
  
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
|— typ|Nazwa typu CLR programu obsługi tokenów, który ma zostać dodany. Aby uzyskać więcej informacji na temat sposobu określania atrybutu `type`, zobacz [odwołania do typów niestandardowych](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement >](samlsecuritytokenrequirement.md)|Zapewnia konfigurację dla klasy <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> lub klasy pochodnej jednej z tych klas.|  
|[\<sessionTokenRequirement >](sessiontokenrequirement.md)|Zapewnia konfigurację dla klasy <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> lub klas pochodnych.|  
|[\<userNameSecurityTokenHandlerRequirement >](usernamesecuritytokenhandlerrequirement.md)|Zapewnia konfigurację dla klasy <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> lub klas pochodnych.|  
|[\<x509SecurityTokenHandlerRequirement >](x509securitytokenhandlerrequirement.md)|Zapewnia opcjonalną konfigurację dla klasy <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> lub klas pochodnych.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<securityTokenHandler >](securitytokenhandlers.md)|Określa kolekcję programów obsługi tokenów zabezpieczających, które są zarejestrowane w punkcie końcowym.|  
  
## <a name="remarks"></a>Uwagi  
 Element `<add>` może przyjmować jeden element podrzędny, który określa konfigurację programu obsługi tokenów. Jest to zależne od tego, czy Klasa obsługi, do której odwołuje się atrybut `type` elementu `<add>`, zapewnia obsługę tej funkcji. Klasy obsługi tokenów, które udostępniają tę funkcję, muszą uwidaczniać konstruktora, który przyjmuje obiekt <xref:System.Xml.XmlElement>.  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Niektóre wbudowane klasy procedury obsługi tokenów zabezpieczających zapewniają tę funkcję. Te klasy to <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>i <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.  
  
> [!IMPORTANT]
> Kolekcja obsługi tokenów może zawierać tylko jedną procedurę obsługi dla danego typu. Oznacza to, na przykład, że jeśli chcesz dodać program obsługi, który pochodzi od klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> do kolekcji, musisz najpierw usunąć <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, który jest domyślnie obecny, z kolekcji. Można użyć elementu [\<remove >](remove.md) , aby usunąć pojedynczą procedurę obsługi z kolekcji lub użyć elementu [\<Clear >](clear.md) , aby usunąć wszystkie programy obsługi z kolekcji.  
  
 Ustawienia określone w przesłonięciu programu obsługi, które zostały określone w kolekcji obsługi tokenów w elemencie [\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) i tych określonych na poziomie usługi w ramach elementu [\<IdentityConfiguration >](identityconfiguration.md) .  
  
## <a name="example"></a>Przykład  
 Poniższy kod XML pokazuje użycie `<add>` i `<remove>` elementów, aby zastąpić domyślną procedurę obsługi tokena sesji za pomocą procedury obsługi niestandardowego tokenu sesji. KOD XML jest pobierany z przykładu `ClaimsAwareWebFarm`.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
