---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 50fc7194823fb0c5c426fb54ffd50b17c3714ed9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251760"
---
# \<trustedIssuers>
Konfiguruje listę certyfikatów zaufanych wystawców używanych przez rejestr nazw wystawcy oparty na konfiguracji ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> ).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|Dodaje certyfikat do kolekcji zaufanych wystawców. Certyfikat jest określony przy użyciu `thumbprint` atrybutu. Ten atrybut jest wymagany i powinien zawierać postać zaszyfrowanego numeru ASN. 1 odcisku palca certyfikatu. `name`Atrybut jest opcjonalny i może służyć do określenia przyjaznej nazwy certyfikatu.|  
|`<clear>`|Czyści wszystkie certyfikaty z kolekcji zaufanych wystawców.|  
|`<remove thumbprint=xs:string>`|Usuwa certyfikat z kolekcji zaufanych wystawców. Certyfikat jest określony przy użyciu `thumbprint` atrybutu. Ten atrybut jest wymagany.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|Konfiguruje rejestr nazwy wystawcy. **Ważne:**  `type`Atrybut `<issuerNameRegistry>` elementu musi odwoływać się do <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy, aby `<trustedIssuers>` element był prawidłowy.|  
  
## <a name="remarks"></a>Uwagi  
 Program Windows Identity Foundation (WIF) udostępnia jedną implementację <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy z pola, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy. Nazwa wystawcy konfiguracji rejestru przechowuje listę zaufanych wystawców, które są ładowane z konfiguracji. Lista kojarzy nazwy poszczególnych wystawców z certyfikatem X. 509, który jest wymagany do zweryfikowania podpisu tokenów wygenerowanych przez wystawcę. Lista zaufanych certyfikatów wystawcy jest określona w `<trustedIssuers>` elemencie. Każdy element na liście kojarzy nazwę wystawcy z certyfikatem X. 509, który jest niezbędny do zweryfikowania sygnatury tokenów wytworzonych przez tego wystawcy. Certyfikaty zaufane są określane przy użyciu formy z certyfikatem ASN. 1 i są dodawane do kolekcji za pomocą `<add>` elementu. Wystawcy (certyfikaty) można wyczyścić lub usunąć z listy za pomocą `<clear>` `<remove>` elementów i.  
  
 `type`Atrybut `<issuerNameRegistry>` elementu musi odwoływać się do <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy, aby `<trustedIssuers>` element był prawidłowy.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie XML pokazano, jak określić nazwę rejestru wystawcy na podstawie konfiguracji.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
