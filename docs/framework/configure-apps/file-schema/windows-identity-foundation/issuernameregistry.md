---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 209e702da80f2569f2b6c068f50f1af4489157f6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251963"
---
# \<issuerNameRegistry>
Konfiguruje rejestr nazw wystawców, który jest używany przez programy obsługi w kolekcji obsługi tokenów.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
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
|typ|Typ, który pochodzi od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy. Aby uzyskać więcej informacji na temat sposobu określania niestandardowego `type` , zobacz [odwołania do typów niestandardowych].|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|Gdy `type` atrybut określa rejestr nazw wystawcy oparty na konfiguracji ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> Klasa), [\<trustedIssuers>](trustedissuers.md) należy określić element. [\<trustedIssuers>](trustedissuers.md)Element może przyjmować `<add>` , `<clear>` , lub `<remove>` elementy jako elementy podrzędne.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie tokeny wystawcy są weryfikowane przy użyciu rejestru nazwy wystawcy. Jest to obiekt, który pochodzi od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy. Rejestr nazwy wystawcy służy do kojarzenia nazwy z materiałem kryptograficznym, który jest niezbędny do zweryfikowania podpisów tokenów wytworzonych przez odpowiedniego wystawcy. Nazwa wystawcy Rejestr zawiera listę wystawców, które są zaufane przez aplikację jednostki uzależnionej (RP). Typ rejestru Nazwa wystawcy jest określany przy użyciu `type` atrybutu. `<issuerNameRegistry>`Element może mieć co najmniej jeden element podrzędny, który zapewnia konfigurację określonego typu. Należy podać logikę, która przetwarza te elementy podrzędne, zastępując <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> metodę.  
  
 WIF zawiera typ rejestru o pojedynczej nazwie wystawcy z pola, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> Klasa. Ta klasa używa zestawu certyfikatów zaufanych wystawców, które są określone w konfiguracji. Wymaga podrzędnego elementu konfiguracji, `<trustedIssuers>` w którym jest skonfigurowana kolekcja certyfikatów zaufanych wystawców. Certyfikaty zaufane są określane przy użyciu formy z certyfikatem ASN. 1 zaszyfrowanego odcisku palca certyfikatu i są dodawane lub usuwane z kolekcji przy użyciu `<add>` `<clear>` elementów, lub `<remove>` .  
  
 `<issuerNameRegistry>`Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> klasę.  
  
> [!NOTE]
> Określanie `<issuerNameRegistry>` elementu jako elementu podrzędnego [\<identityConfiguration>](identityconfiguration.md) elementu jest przestarzałe, ale nadal jest ono obsługiwane w celu zapewnienia zgodności z poprzednimi wersjami. Ustawienia w `<securityTokenHandlerConfiguration>` elemencie Przesłoń te elementy w `<identityConfiguration>` elemencie.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie XML pokazano, jak określić nazwę rejestru wystawcy na podstawie konfiguracji.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
