---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152635"
---
# <a name="samlsecuritytokenrequirement"></a>\<samlSecurityTokenOkiwkość>
Zawiera konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> dla <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy, klasy lub klasy pochodnej jednej z tych klas. Reprezentowana przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasę.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>securityTokenHandlers**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dodaj>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenOkiwkość>**  
  
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
|mapToWindows|Określa, czy program obsługi tokenu powinien mapować token sprawdzania poprawności na konto systemu Windows przy użyciu przychodzącego oświadczenia upn. Wartość domyślna to "false".|  
|issuerCertificateRevocationMode|Wartość <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> określająca tryb odwołania do użycia dla certyfikatu X.509. Wartością domyślną jest "Online".|  
|issuerCertificateValidationMode|Wartość <xref:System.ServiceModel.Security.X509CertificateValidationMode> określająca tryb sprawdzania poprawności dla certyfikatu X.509. Wartością domyślną jest "PeerOrChainTrust".|  
|issuerCertificateTrustedStoreLokation|Wartość <xref:System.Security.Cryptography.X509Certificates.StoreLocation> określająca magazyn certyfikatów X.509. Wartością domyślną jest "LocalMachine".|  
|issuerCertificateValidator|Typ niestandardowy, który <xref:System.IdentityModel.Selectors.X509CertificateValidator>pochodzi od . Jeśli `issuerCertificateValidationMode` atrybut jest "Niestandardowe", wystąpienie tego typu jest używane do sprawdzania poprawności certyfikatu wystawcy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<nazwaClaimType>](nameclaimtype.md)|Ustawia typ oświadczenia, który <xref:System.Security.Principal.IIdentity.Name%2A> określa właściwość.|  
|[\<>roleClaimType](roleclaimtype.md)|Określa typ oświadczenia, który definiuje oświadczenia typu roli <xref:System.Security.Claims.ClaimsIdentity> w kolekcji obiektów zwracanych przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodę obsługi tokenu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dodaj>](add.md)|Dodaje określony program obsługi tokenu zabezpieczającego do kolekcji obsługi tokenów.|  
  
## <a name="remarks"></a>Uwagi  
 Element `<samlSecurityTokenRequirement>` jest reprezentowany <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> przez klasę w modelu obiektu i `SamlSecurityTokenRequirement` służy do <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> konfigurowania właściwości na a lub <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.  
  
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
