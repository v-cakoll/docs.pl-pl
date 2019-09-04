---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 8775e3044e58886cfa53a9fd9fc8b4b8ed2105b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251953"
---
# <a name="issuertokenresolver"></a>\<issuerTokenResolver>
Rejestruje program rozpoznawania tokenów wystawcy, który jest używany przez programy obsługi w kolekcji obsługi tokenów. Program rozpoznawania tokenów wystawcy służy do rozpoznawania tokenu podpisywania w przypadku przychodzących tokenów i komunikatów.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerTokenResolver >**  
  
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
|— typ|Określa typ programu rozpoznawania tokenów wystawcy. Musi być <xref:System.IdentityModel.Tokens.IssuerTokenResolver> klasą lub typem, który pochodzi <xref:System.IdentityModel.Tokens.IssuerTokenResolver> od klasy. Wymagana.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.|  
  
## <a name="remarks"></a>Uwagi  
 Program rozpoznawania tokenów wystawcy służy do rozpoznawania tokenu podpisywania w przypadku przychodzących tokenów i komunikatów. Służy do pobierania materiału kryptograficznego, który jest używany do sprawdzania podpisu. Należy określić `type` atrybut. Określony typ może być albo <xref:System.IdentityModel.Tokens.IssuerTokenResolver> typem niestandardowym, który pochodzi <xref:System.IdentityModel.Tokens.IssuerTokenResolver> od klasy.  
  
 Niektóre programy obsługi tokenów umożliwiają określenie ustawień programu rozpoznawania tokenów wystawcy w konfiguracji. Ustawienia poszczególnych programów obsługi tokenów przesłaniają te określone w kolekcji obsługi tokenów zabezpieczających.  
  
> [!NOTE]
> Określanie elementu jako elementu [ \<](identityconfiguration.md) podrzędnego elementu IdentityConfiguration > jest przestarzałe, ale nadal jest on obsługiwany w celu zapewnienia zgodności z poprzednimi wersjami. `<issuerTokenResolver>` Ustawienia w `<securityTokenHandlerConfiguration>` elemencie Przesłoń te elementy `<identityConfiguration>` w elemencie.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie XML przedstawiono konfigurację programu rozpoznawania tokenów wystawcy opartą na niestandardowej klasie, która <xref:System.IdentityModel.Tokens.IssuerTokenResolver>pochodzi od. Program rozpoznawania tokenów obsługuje słownik par kluczy odbiorców, które są inicjowane z niestandardowego elementu konfiguracji (`<AddAudienceKeyPair>`) zdefiniowanego dla klasy. Klasa przesłania <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metodę w celu przetworzenia tego elementu. Przesłonięcie pokazano w następującym przykładzie: jednak metody, które wywołuje, nie są wyświetlane dla zwięzłości. Aby uzyskać pełny przykład, zobacz `CustomToken` przykład.  
  
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
