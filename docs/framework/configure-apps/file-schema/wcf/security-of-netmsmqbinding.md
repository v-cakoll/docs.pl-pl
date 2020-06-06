---
title: <security> dla <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 7877fd59aff581eee5b62a1ca224dbf51c956069
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738670"
---
# <a name="security-of-netmsmqbinding"></a>\<security> dla \<netMsmqBinding>
Definiuje ustawienia zabezpieczeń dla powiązania usługi MSMQ. Określa, czy zabezpieczenia transportu lub protokołu SOAP są włączone i, jeśli tak, jakiego trybu uwierzytelniania i poziomów ochrony są używane.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<security mode="None/Transport/Message/Both">
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
             clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|tryb|Określa typ zabezpieczeń, który kontroluje integralność, poufność i uwierzytelnianie. Prawidłowe wartości to:<br /><br /> -Brak: spowoduje to wyłączenie zabezpieczeń.<br />-Transport: Ochrona i uwierzytelnianie są oferowane przez transport. Ma to zastosowanie do zabezpieczeń komunikatów między dwoma menedżerami kolejki. Nie ma żadnych zabezpieczeń oferowanych między aplikacją a menedżerem kolejki. Istniejące aplikacje MSMQ są funkcjonalnie równoważne z tego typu trybem zabezpieczeń.<br />-Message: Określa zabezpieczenia aplikacji końcowej. Warstwa transportu nie oferuje żadnych zabezpieczeń. Jest to podobne do zabezpieczeń oferowanych przez inne powiązania standardowe.<br />-Both: oferuje zabezpieczenia zarówno dla warstwy transportu, jak i protokołu SOAP. To samo poświadczenie jest wymagane na poziomie.<br /><br /> Wartością domyślną jest transport. Ten atrybut jest typu <xref:System.ServiceModel.NetMsmqSecurityMode> .|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<message>](message-of-netmsmqbinding.md)|Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP. Ten element jest typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement> .|  
|[\<transport>](transport-of-netmsmqbinding.md)|Definiuje ustawienia zabezpieczeń dla transportu MSMQ. Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> .|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|powiązanie|Element Binding elementu[\<netMsmqBinding>](netmsmqbinding.md)|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [Kolejki programu WCF](../../../wcf/feature-details/queues-in-wcf.md)
