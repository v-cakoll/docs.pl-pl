---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: bb4cb5178885b90ef25ee827c2f11593ead6e73d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354560"
---
# <a name="trustedissuers"></a>\<trustedIssuers>
Umożliwia skonfigurowanie listy zaufanych wystawców certyfikatów używane przez rejestru nazwy wystawcy oparta na konfiguracji (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<issuerNameRegistry>  
\<trustedIssuers>  
  
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
|`<add thumbprint=xs:string name=xs:string>`|Dodaje certyfikat do kolekcji zaufanych wystawców. Certyfikat jest określony za pomocą `thumbprint` atrybutu. Ten atrybut jest wymagany i może zawierać formularz ASN.1 zakodowane odcisk palca certyfikatu. `name` Atrybut jest opcjonalny i może służyć do Podaj przyjazną nazwę certyfikatu.|  
|`<clear>`|Czyści wszystkie certyfikaty z kolekcji zaufanych wystawców.|  
|`<remove thumbprint=xs:string>`|Usuwa certyfikat z kolekcji zaufanych wystawców. Certyfikat jest określony za pomocą `thumbprint` atrybutu. Ten atrybut jest wymagany.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Konfiguruje rejestru nazwy wystawcy. **Ważne:**  `type` Atrybutu `<issuerNameRegistry>` musi odwoływać się do elementu <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy dla `<trustedIssuers>` element był prawidłowy.|  
  
## <a name="remarks"></a>Uwagi  
 Windows Identity Foundation (WIF) udostępnia pojedynczą implementacją <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy gotowych, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy. Rejestru nazwy wystawcy konfiguracji utrzymuje listę zaufanych wystawców, który jest ładowany z konfiguracji. Lista kojarzy nazwy wystawcy przy użyciu certyfikatu X.509, który jest potrzebny do weryfikowania podpisu produkowane przez wystawcy tokenów. Lista zaufanych wystawców certyfikatów jest określony w sekcji `<trustedIssuers>` elementu. Każdy element na liście kojarzy nazwę wystawcy mnemoników przy użyciu certyfikatu X.509, które są potrzebne do zweryfikowania podpisu generowane przez ten wystawcy tokenów. Zaufane certyfikaty są określane przy użyciu ASN.1 zakodowane w postaci odcisku palca certyfikatu i są dodawane kolekcji przy użyciu `<add>` elementu. Możesz wyczyścić, lub usunąć wystawców (certyfikatów) z listy przy użyciu `<clear>` i `<remove>` elementów.  
  
 `type` Atrybutu `<issuerNameRegistry>` musi odwoływać się do elementu <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy dla `<trustedIssuers>` element był prawidłowy.  
  
## <a name="example"></a>Przykład  
 Następujący kod XML pokazuje sposób określania wystawcy konfiguracji na podstawie nazwy rejestru.  
  
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
