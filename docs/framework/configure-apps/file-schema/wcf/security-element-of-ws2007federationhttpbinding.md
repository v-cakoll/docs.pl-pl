---
title: '&lt;security&gt; w &lt;ws2007FederationHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 0358b8cd0ddc91baf4028fa8a3f06d032c3f117b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-element-of-ltws2007federationhttpbindinggt"></a>&lt;security&gt; w &lt;ws2007FederationHttpBinding&gt;
Definiuje ustawienia zabezpieczeń [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementu.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<ws2007FederationHttpBinding>  
\<Powiązanie >  
\<security>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<ws2007FederationBinding>  
    <binding >  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                defaultProtectionLevel="none/sign/EncryptAndSign"   
                issuedTokenType="string"   
                issuedKeyType="SymmetricKey/PublicKey"  
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
|`mode`|Opcjonalny. Określa typ zabezpieczeń, która została zastosowana. Wartość domyślna to `Message`. Ten atrybut jest typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>Tryb atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Komunikatu protokołu SOAP nie jest bezpieczne podczas przesyłania.|  
|Komunikat|Korzystanie z zabezpieczeń komunikatów SOAP są udostępniane integralności, poufność, uwierzytelnianie serwera i uwierzytelnianie klienta. Domyślnie treści zostaje zaszyfrowany i podpisany. Usługa musi być skonfigurowana przy użyciu certyfikatu. Uwierzytelnianie klienta jest oparta na token wystawiony do klienta przez usługę tokenu zabezpieczającego.|  
|TransportWithMessageCredential|Uwierzytelnianie integralności i poufności serwera są udostępniane przez protokół HTTPS. Usługa musi być skonfigurowana przy użyciu certyfikatu. Uwierzytelnianie klienta jest dostarczany za pomocą zabezpieczeń wiadomości SOAP i opierają się na token wystawiony do klienta przez usługę tokenu zabezpieczającego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|Definiuje ustawienia zabezpieczeń na poziomie wiadomości. Ten element jest typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [Instrukcje: tworzenie elementu WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Wybieranie typu poświadczeń](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
