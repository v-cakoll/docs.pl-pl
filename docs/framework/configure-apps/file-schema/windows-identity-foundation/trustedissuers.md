---
title: '&lt;trustedIssuers&gt;'
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f9daea7d6b78e2f6790050b35dde62db6058c60b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="lttrustedissuersgt"></a>&lt;trustedIssuers&gt;
Umożliwia skonfigurowanie listy zaufanych wystawców certyfikatów używanych przez wystawców na podstawie konfiguracji rejestru nazwy (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).  
  
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
|`<add thumbprint=xs:string name=xs:string>`|Dodaje certyfikat do kolekcji zaufanych wystawców. Certyfikat zostanie określony z `thumbprint` atrybutu. Ten atrybut jest wymagany i musi zawierać formularza kodowane ASN.1 odcisk palca certyfikatu. `name` Atrybutu jest opcjonalny i może służyć do Określ przyjazną nazwę certyfikatu.|  
|`<clear>`|Usuwa wszystkie certyfikaty z kolekcji zaufanych wystawców.|  
|`<remove thumbprint=xs:string>`|Usuwa certyfikat z kolekcji zaufanych wystawców. Certyfikat zostanie określony z `thumbprint` atrybutu. Ten atrybut jest wymagany.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Konfiguruje rejestru nazwy dostawcy. **Ważne:** `type` atrybutu `<issuerNameRegistry>` element musi odwoływać się <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy dla `<trustedIssuers>` elementu jest nieprawidłowy.|  
  
## <a name="remarks"></a>Uwagi  
 Windows Identity Foundation (WIF) zawiera pojedynczą implementacją właściwości <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy fabrycznej, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy. Rejestru nazwy dostawcy konfiguracji przechowuje listę zaufanych wystawców, które są ładowane z konfiguracji. Listy kojarzy nazwy wystawcy z certyfikatu X.509, który jest potrzebne do zweryfikowania podpisu utworzonego przez wystawcy tokenów. Lista zaufanych wystawców certyfikatów jest określony w `<trustedIssuers>` elementu. Każdy element na liście kojarzy nazwę skrótu wystawcy z certyfikatu X.509, który jest potrzebny do zweryfikowania podpisu utworzone przez tego wystawcy tokenów. Zaufane certyfikaty są określone za pomocą ASN.1 zakodowane formularza odcisk palca certyfikatu i są dodawane kolekcji przy użyciu `<add>` elementu. Możesz wyczyścić lub Usuń z listy wystawców (certyfikatów), za pomocą `<clear>` i `<remove>` elementy.  
  
 `type` Atrybutu `<issuerNameRegistry>` element musi odwoływać się <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy dla `<trustedIssuers>` elementu jest nieprawidłowy.  
  
## <a name="example"></a>Przykład  
 Następujący kod XML pokazano, jak określić wystawcę na podstawie konfiguracji rejestru nazwy.  
  
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
