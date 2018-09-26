---
title: '&lt;trustedIssuers&gt;'
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: c390cecc265b27dfa8d9d0a892f5930c982f7054
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075375"
---
# <a name="lttrustedissuersgt"></a>&lt;trustedIssuers&gt;
Umożliwia skonfigurowanie listy zaufanych wystawców certyfikatów używane przez rejestru nazwy wystawcy oparta na konfiguracji (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration >  
\<issuerNameRegistry >  
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
|`<add thumbprint=xs:string name=xs:string>`|Dodaje certyfikat do kolekcji zaufanych wystawców. Certyfikat jest określony za pomocą `thumbprint` atrybutu. Ten atrybut jest wymagany i może zawierać formularz ASN.1 zakodowane odcisk palca certyfikatu. `name` Atrybut jest opcjonalny i może służyć do Podaj przyjazną nazwę certyfikatu.|  
|`<clear>`|Czyści wszystkie certyfikaty z kolekcji zaufanych wystawców.|  
|`<remove thumbprint=xs:string>`|Usuwa certyfikat z kolekcji zaufanych wystawców. Certyfikat jest określony za pomocą `thumbprint` atrybutu. Ten atrybut jest wymagany.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Konfiguruje rejestru nazwy wystawcy. **Ważne:** `type` atrybutu `<issuerNameRegistry>` musi odwoływać się do elementu <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy dla `<trustedIssuers>` element był prawidłowy.|  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
