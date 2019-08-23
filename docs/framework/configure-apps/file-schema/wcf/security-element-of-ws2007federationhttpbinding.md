---
title: <security>elementu<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 61b56ca1fae5c328cda0bbebef4026f0784095a3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936819"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a>\<> zabezpieczeń elementu \<WS2007FederationHttpBinding >
Definiuje ustawienia [ \<zabezpieczeń elementu > WS2007FederationHttpBinding](ws2007federationhttpbinding.md) .  
  
 \<system.ServiceModel>  
\<> powiązań  
\<ws2007FederationHttpBinding>  
\<> powiązania  
\<> zabezpieczeń  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`mode`|Opcjonalna. Określa typ stosowanego zabezpieczenia. Wartość domyślna to `Message`. Ten atrybut jest typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>Atrybut Mode  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Komunikat protokołu SOAP nie jest zabezpieczony podczas transferu.|  
|Message|Integralność, poufność, uwierzytelnianie serwera i uwierzytelnianie klienta są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP. Domyślnie treść jest zaszyfrowana i podpisana. Usługa musi być skonfigurowana przy użyciu certyfikatu. Uwierzytelnianie klienta opiera się na tokenie wystawionym dla klienta przez usługę tokenu zabezpieczającego.|  
|TransportWithMessageCredential|Uwierzytelnianie za pomocą protokołu HTTPS zapewnia integralność, poufność i serwer. Usługa musi być skonfigurowana przy użyciu certyfikatu. Uwierzytelnianie klienta jest zapewniane przez zabezpieczenia komunikatów protokołu SOAP i opiera się na tokenie wystawionym dla klienta przez usługę tokenu zabezpieczającego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<message>](message-of-ws2007httpbinding.md)|Definiuje ustawienia zabezpieczeń na poziomie wiadomości. Ten element jest typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> powiązania](../../../misc/binding.md)|Definiuje wszystkie możliwości [ \<powiązań WSDualHttpBinding >](wsdualhttpbinding.md).|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [Instrukcje: Utwórz WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Wybieranie typu poświadczeń](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> powiązania](../../../misc/binding.md)
