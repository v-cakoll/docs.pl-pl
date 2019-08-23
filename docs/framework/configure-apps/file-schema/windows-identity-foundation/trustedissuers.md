---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 32aad3529ded6d0234b1bcb388ecbbc3b0a11c87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944272"
---
# <a name="trustedissuers"></a>\<trustedIssuers >
Konfiguruje listę certyfikatów zaufanych wystawców używanych przez rejestr nazw wystawcy oparty na konfiguracji<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>().  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<issuerNameRegistry>  
\<trustedIssuers >  
  
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
|`<add thumbprint=xs:string name=xs:string>`|Dodaje certyfikat do kolekcji zaufanych wystawców. Certyfikat jest określony przy użyciu `thumbprint` atrybutu. Ten atrybut jest wymagany i powinien zawierać postać zaszyfrowanego numeru ASN. 1 odcisku palca certyfikatu. `name` Atrybut jest opcjonalny i może służyć do określenia przyjaznej nazwy certyfikatu.|  
|`<clear>`|Czyści wszystkie certyfikaty z kolekcji zaufanych wystawców.|  
|`<remove thumbprint=xs:string>`|Usuwa certyfikat z kolekcji zaufanych wystawców. Certyfikat jest określony przy użyciu `thumbprint` atrybutu. Ten atrybut jest wymagany.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|Konfiguruje rejestr nazwy wystawcy. **Ważne:**  Atrybut elementu musi odwoływać się <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> do klasy, `<trustedIssuers>` aby element był prawidłowy. `<issuerNameRegistry>` `type`|  
  
## <a name="remarks"></a>Uwagi  
 Program Windows Identity Foundation (WIF) udostępnia jedną implementację <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy z pola, klasy.<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> Nazwa wystawcy konfiguracji rejestru przechowuje listę zaufanych wystawców, które są ładowane z konfiguracji. Lista kojarzy nazwy poszczególnych wystawców z certyfikatem X. 509, który jest wymagany do zweryfikowania podpisu tokenów wygenerowanych przez wystawcę. Lista zaufanych certyfikatów wystawcy jest określona w `<trustedIssuers>` elemencie. Każdy element na liście kojarzy nazwę wystawcy z certyfikatem X. 509, który jest niezbędny do zweryfikowania sygnatury tokenów wytworzonych przez tego wystawcy. Certyfikaty zaufane są określane przy użyciu formy z certyfikatem ASN. 1 i są dodawane do kolekcji `<add>` za pomocą elementu. Wystawcy (certyfikaty) można wyczyścić lub usunąć z listy za pomocą `<clear>` elementów i. `<remove>`  
  
 Atrybut elementu musi odwoływać się <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> do klasy, `<trustedIssuers>` aby element był prawidłowy. `<issuerNameRegistry>` `type`  
  
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
