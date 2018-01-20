---
title: '&lt;security&gt; w &lt;netMsmqBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: fb381d6970d72cc1ff88ed1238d8d8541c40a40d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltnetmsmqbindinggt"></a>&lt;security&gt; w &lt;netMsmqBinding&gt;
Definiuje ustawienia zabezpieczeń dla powiązania usługi MSMQ. Określa, czy włączono transportu lub zabezpieczeń protokołu SOAP, a jeśli tak, poziomy tryb i ochrony uwierzytelniania są używane.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netMsmqBinding>  
\<Powiązanie >  
\<security>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<security mode="None/Transport/Message/Both">  
   <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
      msmqEncryptionAlgorithm="RC4Stream/AES"  
      msmqProtectionLevel="None/Sign/EncryptAndSign"  
      msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
      <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|tryb|Określa typ zabezpieczeń, która kontroluje, integralności i poufności uwierzytelniania. Prawidłowe wartości są następujące:<br /><br /> -Brak: Powoduje wyłączenie zabezpieczeń.<br />-Transport: Ochrony i uwierzytelniania są oferowane przez transport. Dotyczy to zabezpieczenia wiadomości między menedżerami kolejki dwa. Nie ma żadnych zabezpieczeń oferowany między aplikacją a menedżera kolejek. Istniejące aplikacje usługi Msmq są taką samą funkcję z tym typem tryb zabezpieczeń.<br />-Komunikat o błędzie: Określa trasie zabezpieczeń aplikacji. Nie ma żadnych zabezpieczeń oferowanych w warstwie transportowej. Jest to podobne do zabezpieczeń oferowanych przez inne standardowe powiązania.<br />-Zarówno: Oferuje zabezpieczeń transportu i protokołu SOAP wiadomości warstwy. Tych samych poświadczeń jest wymagany na obu poziomach.<br /><br /> Wartość domyślna to transportu. Ten atrybut jest typu <xref:System.ServiceModel.NetMsmqSecurityMode>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP. Ten element jest typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.|  
|[\<transport >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|Definiuje ustawienia zabezpieczeń dla transportu MSMQ. Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|powiązanie|Element powiązania [ \<netMsmqBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>  
 <xref:System.ServiceModel.NetMsmqBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)  
 [Kolejki programu WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
