---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152674"
---
# <a name="issuertokenresolver"></a>\<>>
Rejestruje program rozpoznawania nazw tokenów wystawcy, który jest używany przez programy obsługi w kolekcji obsługi tokenu. Program rozpoznawania nazw tokenów wystawcy służy do rozpoznawania tokenu podpisywania na przychodzących tokenach i wiadomościach.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>securityTokenHandlers**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji securityTokenHandler**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>>**  
  
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
|type|Określa typ programu rozpoznawania tokenów wystawcy. Musi być klasą <xref:System.IdentityModel.Tokens.IssuerTokenResolver> lub typem, który <xref:System.IdentityModel.Tokens.IssuerTokenResolver> wywodzi się z klasy. Wymagany.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>konfiguracji securityTokenHandler](securitytokenhandlerconfiguration.md)|Zapewnia konfigurację dla kolekcji obsługi tokenów zabezpieczających.|  
  
## <a name="remarks"></a>Uwagi  
 Program rozpoznawania nazw tokenów wystawcy służy do rozpoznawania tokenu podpisywania na przychodzących tokenach i wiadomościach. Służy do pobierania materiału kryptograficznego, który jest używany do sprawdzania podpisu. Należy określić `type` atrybut. Określony typ może być <xref:System.IdentityModel.Tokens.IssuerTokenResolver> albo typu niestandardowego, <xref:System.IdentityModel.Tokens.IssuerTokenResolver> który pochodzi od klasy.  
  
 Niektóre programy obsługi tokenu umożliwiają określenie ustawień rozpoznawania nazw tokenów wystawcy w konfiguracji. Ustawienia poszczególnych programów obsługi tokenów zastępują te określone w kolekcji obsługi tokenów zabezpieczających.  
  
> [!NOTE]
> Określanie `<issuerTokenResolver>` elementu jako elementu podrzędnego [ \<identityConfiguration>](identityconfiguration.md) element został przestarzały, ale nadal jest obsługiwany dla zgodności z powrotem. Ustawienia elementu `<securityTokenHandlerConfiguration>` zastąpić te na `<identityConfiguration>` elemencie.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XML przedstawia konfigurację programu rozpoznawania tokenów wystawcy, <xref:System.IdentityModel.Tokens.IssuerTokenResolver>która jest oparta na klasie niestandardowej, która wywodzi się z . Program rozpoznawania nazw tokenów przechowuje słownik par klucza odbiorców, który jest`<AddAudienceKeyPair>`inicjowany z niestandardowego elementu konfiguracji ( ) zdefiniowanego dla klasy. Klasa zastępuje <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metodę przetwarzania tego elementu. Zastąpienie jest pokazane w poniższym przykładzie; jednak metody, które wywołuje, nie są wyświetlane dla zwięzłości. Pełny przykład można znaleźć `CustomToken` w przykładzie.  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a>Przykład
  
```csharp
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
