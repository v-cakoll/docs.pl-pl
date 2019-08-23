---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 8185153eb02c5794b0f6ac02a6837806f2073c07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941920"
---
# <a name="certificatevalidation"></a>\<certificateValidation>
Kontroluje ustawienia używane przez programy obsługi do sprawdzania poprawności certyfikatów. Te ustawienia są zastępowane, jeśli określony program obsługi jest skonfigurowany przy użyciu własnego modułu sprawdzania poprawności.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<certificateValidation>  
  
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
|certificateValidationMode|<xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość określająca tryb walidacji, który ma być używany dla certyfikatu X. 509. Wartość domyślna to "PeerOrChainTrust". Aby określić niestandardowy moduł sprawdzania poprawności, ustaw ten atrybut na "niestandardowy" i określ moduł walidacji przy użyciu [ \<elementu certificateValidator >](certificatevalidator.md) . Opcjonalny.|  
|odwołaniemode|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość określająca tryb odwołania, który ma być używany dla certyfikatu X. 509. Wartość domyślna to "online". Opcjonalna.|  
|trustedStoreLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation> Wartość określająca magazyn certyfikatów X. 509. Wartość domyślna to "LocalMachine". Opcjonalny.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<certificateValidator >](certificatevalidator.md)|Określa typ niestandardowy na potrzeby walidacji certyfikatu. Ten typ jest używany tylko wtedy, `certificateValidationMode` gdy atrybut [ \<elementu certificateValidation >](certificatevalidation.md) jest ustawiony na wartość "Custom".|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Określa ustawienia tożsamości na poziomie usług.|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.|  
  
## <a name="remarks"></a>Uwagi  
 Element można określić na poziomie usługi `<identityConfiguration>` pod elementem lub na poziomie kolekcji `<securityTokenHandlerConfiguration>` programu obsługi tokenów zabezpieczających w ramach elementu. `<certificateValidation>` Ustawienia w kolekcji obsługi tokenów zastępują te określone w usłudze. Niektóre programy obsługi tokenów umożliwiają określanie ustawień weryfikacji certyfikatu w konfiguracji. Ustawienia poszczególnych programów obsługi tokenów przesłaniają te określone zarówno na poziomie usługi, jak i w kolekcji obsługi tokenów zabezpieczających.  
  
## <a name="example"></a>Przykład  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
