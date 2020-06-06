---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: c2d1a5d36cb5616ef06eedc093dd70a68a164a81
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252139"
---
# \<certificateValidation>
Kontroluje ustawienia używane przez programy obsługi do sprawdzania poprawności certyfikatów. Te ustawienia są zastępowane, jeśli określony program obsługi jest skonfigurowany przy użyciu własnego modułu sprawdzania poprawności.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|certificateValidationMode|Wartość określająca <xref:System.ServiceModel.Security.X509CertificateValidationMode> tryb walidacji, który ma być używany dla certyfikatu X. 509. Wartość domyślna to "PeerOrChainTrust". Aby określić niestandardowy moduł sprawdzania poprawności, ustaw ten atrybut na "niestandardowy" i określ moduł walidacji przy użyciu [\<certificateValidator>](certificatevalidator.md) elementu. Opcjonalny.|  
|odwołaniemode|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>Wartość określająca tryb odwołania, który ma być używany dla certyfikatu X. 509. Wartość domyślna to "online". Opcjonalny.|  
|trustedStoreLocation|Wartość określająca <xref:System.Security.Cryptography.X509Certificates.StoreLocation> Magazyn certyfikatów X. 509. Wartość domyślna to "LocalMachine". Opcjonalny.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<certificateValidator>](certificatevalidator.md)|Określa typ niestandardowy na potrzeby walidacji certyfikatu. Ten typ jest używany tylko wtedy, gdy `certificateValidationMode` atrybut [\<certificateValidation>](certificatevalidation.md) elementu jest ustawiony na wartość "Custom".|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Określa ustawienia tożsamości na poziomie usług.|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.|  
  
## <a name="remarks"></a>Uwagi  
 `<certificateValidation>`Element można określić na poziomie usługi pod `<identityConfiguration>` elementem lub na poziomie kolekcji programu obsługi tokenów zabezpieczających w ramach `<securityTokenHandlerConfiguration>` elementu. Ustawienia w kolekcji obsługi tokenów zastępują te określone w usłudze. Niektóre programy obsługi tokenów umożliwiają określanie ustawień weryfikacji certyfikatu w konfiguracji. Ustawienia poszczególnych programów obsługi tokenów przesłaniają te określone zarówno na poziomie usługi, jak i w kolekcji obsługi tokenów zabezpieczających.  
  
## <a name="example"></a>Przykład  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
