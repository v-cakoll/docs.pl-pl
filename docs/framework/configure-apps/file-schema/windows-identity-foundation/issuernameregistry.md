---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: ae263a4590cc523c64306ff5d53e54b5190ca510
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202524"
---
# <a name="issuernameregistry"></a>\<issuerNameRegistry>
Konfiguruje rejestru nazwy wystawcy, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<issuerNameRegistry>  
  
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
|— typ|Typ, który pochodzi od klasy <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy. Aby uzyskać więcej informacji o sposobie określania niestandardowej `type`, zobacz [odwołań do niestandardowego typu].|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|Gdy `type` atrybut określa rejestru nazwy wystawcy oparta na konfiguracji ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy), [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element musi być określona. [ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) elementu może potrwać `<add>`, `<clear>`, lub `<remove>` jako elementy podrzędne.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie tokeny wystawcy są weryfikowane za pomocą rejestru nazwy wystawcy. Jest to obiekt, który pochodzi od klasy <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy. Rejestru nazwy wystawcy jest używany do kojarzenia mnemoników nazwy do materiałami kryptograficznymi, potrzebnego do weryfikowania podpisów tokenów produkowane przez odpowiednie wystawcy. Rejestru nazwy wystawcy utrzymuje listę wystawców, które są zaufane przez aplikację jednostki uzależnionej (RP). Typ rejestru nazwy wystawcy jest określony, przy użyciu `type` atrybutu. `<issuerNameRegistry>` Element może mieć elementów podrzędnych, które zapewniają konfiguracji dla określonego typu. Zapewnić logikę, która przetwarza te elementy podrzędne, zastępowanie <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> metody.  
  
 Program WIF oferuje wystawcy pojedynczy typ rejestru nazwy gotowych, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy. Ta klasa używa zestawu zaufanych wystawców certyfikatów, które są określone w konfiguracji. Wymaga elementu podrzędnego konfiguracji `<trustedIssuers>`, pod którym kolekcji certyfikatów zaufanych wystawców jest skonfigurowany. Zaufane certyfikaty są określone za pomocą ASN.1 zakodowane w postaci odcisku palca certyfikatu i są dodawane lub usuwane z kolekcji przy użyciu `<add>`, `<clear>`, lub `<remove>` elementów.  
  
 `<issuerNameRegistry>` Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> klasy.  
  
> [!NOTE]
>  Określanie `<issuerNameRegistry>` element jako element podrzędny [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu jest przestarzałe, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami. Ustawienia na `<securityTokenHandlerConfiguration>` elemencie przesłaniają akcje na `<identityConfiguration>` elementu.  
  
## <a name="example"></a>Przykład  
 Następujący kod XML pokazuje sposób określania wystawcy konfiguracji na podstawie nazwy rejestru.  
  
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
