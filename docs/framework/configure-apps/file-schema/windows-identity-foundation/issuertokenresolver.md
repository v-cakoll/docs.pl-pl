---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: a37935fa9302493c0ecaab0f56e1414d44637af6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269227"
---
# <a name="issuertokenresolver"></a>\<issuerTokenResolver>
Rejestruje wystawcy program rozpoznawania tokenów, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów. Program rozpoznawania tokenów wystawcy jest używany do rozpoznawania token podpisujący na przychodzące tokeny i komunikatów.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<issuerTokenResolver>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|— typ|Określa typ program rozpoznawania tokenów wystawcy. Musi być albo <xref:System.IdentityModel.Tokens.IssuerTokenResolver> klasy lub typu, która pochodzi od klasy <xref:System.IdentityModel.Tokens.IssuerTokenResolver> klasy. Wymagana.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.|  
  
## <a name="remarks"></a>Uwagi  
 Program rozpoznawania tokenów wystawcy jest używany do rozpoznawania token podpisujący na przychodzące tokeny i komunikatów. Służy do pobierania materiałami kryptograficznymi, który służy do sprawdzania podpisu. Należy określić `type` atrybutu. Określony typ może być <xref:System.IdentityModel.Tokens.IssuerTokenResolver> lub typ niestandardowy, który pochodzi od klasy <xref:System.IdentityModel.Tokens.IssuerTokenResolver> klasy.  
  
 Niektóre programy obsługi tokenów umożliwiają określanie ustawień program rozpoznawania tokenów wystawcy w konfiguracji. Ustawienia dotyczące programu obsługi tokenów poszczególnych zastąpienia określonej w kolekcji programu obsługi tokenów zabezpieczeń.  
  
> [!NOTE]
>  Określanie `<issuerTokenResolver>` element jako element podrzędny [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu jest przestarzałe, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami. Ustawienia na `<securityTokenHandlerConfiguration>` elemencie przesłaniają akcje na `<identityConfiguration>` elementu.  
  
## <a name="example"></a>Przykład  
 Następujący kody XML pokazuje konfigurację dla wystawcy program rozpoznawania tokenów opartego na klasę niestandardową, która pochodzi od klasy <xref:System.IdentityModel.Tokens.IssuerTokenResolver>. Program rozpoznawania tokenów przechowuje słownika par klucz odbiorców, który jest inicjowany z niestandardowy element konfiguracji (`<AddAudienceKeyPair>`) zdefiniowane dla klasy. Przesłonięć klasy <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metody do przetworzenia tego elementu. Zastąpienie przedstawiono w poniższym przykładzie; jednak metod wywoływanych przez nią nie są wyświetlane w celu skrócenia programu. Aby uzyskać kompletny przykład, zobacz `CustomToken` próbki.  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a>Przykład  
  
```  
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
