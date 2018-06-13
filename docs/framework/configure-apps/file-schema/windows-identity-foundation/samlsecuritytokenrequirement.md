---
title: '&lt;samlSecurityTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 86a9b9dcf0b9f5971e50ff7d1f1c37ca2e5f778a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756530"
---
# <a name="ltsamlsecuritytokenrequirementgt"></a>&lt;samlSecurityTokenRequirement&gt;
Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej każdej z tych klas. Reprezentowane przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasy.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<add>  
\<samlSecurityTokenRequirement >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement   
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|mapToWindows|Określa, czy programu obsługi tokenów należy mapować sprawdzania poprawności tokenu konto systemu Windows przy użyciu nazwy UPN oświadczenia przychodzącego. Wartość domyślna to "false".|  
|issuerCertificateRevocationMode|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość, która określa tryb odwołania dla certyfikatu X.509. Wartość domyślna to "Online".|  
|issuerCertificateValidationMode|<xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość, która określa tryb walidacji do użycia na potrzeby certyfikatów X.509. Wartość domyślna to "PeerOrChainTrust".|  
|issuerCertificateTrustedStoreLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa magazynu certyfikatu X.509. Wartością domyślną jest "Komputer lokalny".|  
|issuerCertificateValidator|Typ niestandardowy, która jest pochodną <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Jeśli `issuerCertificateValidationMode` atrybutu jest "Custom", wystąpienie tego typu jest używany do sprawdzania poprawności wystawcy certyfikatu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<nameClaimType >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|Ustawia typ oświadczenia, która określa <xref:System.Security.Principal.IIdentity.Name%2A> właściwości.|  
|[\<roleClaimType >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|Określa typ oświadczenia, który definiuje oświadczeń Typ roli w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiekty zwrócone przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metody programu obsługi tokenów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Dodaje określony zabezpieczenia programu obsługi tokenów do kolekcji programu obsługi tokenów.|  
  
## <a name="remarks"></a>Uwagi  
 `<samlSecurityTokenRequirement>` Element jest reprezentowana przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasy w modelu obiektów i jest używany do konfigurowania `SamlSecurityTokenRequirement` właściwość <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> lub <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.  
  
## <a name="example"></a>Przykład  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```
