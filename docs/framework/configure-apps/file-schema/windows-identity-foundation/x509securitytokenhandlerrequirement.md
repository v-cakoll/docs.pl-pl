---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152453"
---
# <a name="x509securitytokenhandlerrequirement"></a>\<x509SecurityTokenHandlerOquirement>
Zapewnia opcjonalną <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> konfigurację dla klasy lub klas pochodnych.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>securityTokenHandlers**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dodaj>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerOquirement>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
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
|Certificatevalidationmode|Wartość <xref:System.ServiceModel.Security.X509CertificateValidationMode> określająca tryb sprawdzania poprawności dla certyfikatu X.509. Wartością domyślną jest "PeerOrChainTrust".|  
|mapToWindows|Określa, czy program obsługi tokenu powinien mapować token sprawdzania poprawności na konto systemu Windows przy użyciu przychodzącego oświadczenia upn. Wartość domyślna to "false".|  
|revocationMode|Wartość <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> określająca tryb odwołania do użycia dla certyfikatu X.509. Wartością domyślną jest "Online".|  
|trustedStoreLocation|Wartość <xref:System.Security.Cryptography.X509Certificates.StoreLocation> określająca magazyn certyfikatów X.509. Wartością domyślną jest "LocalMachine".|  
|certificateValidator|Typ niestandardowy, który <xref:System.IdentityModel.Selectors.X509CertificateValidator>pochodzi od . Jeśli `certificateValidationMode` atrybut jest "Niestandardowe", wystąpienie tego typu jest używane do sprawdzania poprawności certyfikatu wystawcy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dodaj>](add.md)|Dodaje określony program obsługi tokenu zabezpieczającego do kolekcji obsługi tokenów.|  
  
## <a name="example"></a>Przykład  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
