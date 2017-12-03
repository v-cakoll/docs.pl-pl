---
title: '&lt;transport&gt; w &lt;netTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5cf7a0aedc1fcd387b4b41233cd7c31b7ec64de4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a>&lt;transport&gt; w &lt;netTcpBinding&gt;
Określa typ zabezpieczenia na poziomie komunikatu wymagania dotyczące punkt końcowy skonfigurowany [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 \<System. ServiceModel >  
\<powiązania >  
\<netTcpBinding >  
\<Powiązanie >  
\<Zabezpieczenia >  
\<transport >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<netTcpBinding>  
    <binding>  
        <security  
         mode="None|Transport|Message|TransportWithMessageCredential">  
            <transport clientCredentialType="None|Windows|Certificate"  
             protectionLevel="None|Sign|EncryptAndSign"             sslProtocols="Tls|Tls11|Tls12">  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Właściwość clientCredentialType|Opcjonalny. Określa typ poświadczenia, które będą używane podczas uwierzytelniania klienta za pomocą zabezpieczeń transportu.<br /><br /> — Wartość domyślna to `Windows`.<br />— Ten atrybut jest typu <xref:System.ServiceModel.TcpClientCredentialType>.|  
|protectionLevel|Opcjonalny. Definiuje zabezpieczeń na poziomie transportu TCP. Podpisywanie wiadomości zmniejsza ryzyko innych firm, manipulowanie wiadomości, gdy są przesyłane. Szyfrowanie zapewnia ochronę poufności poziom danych podczas transportu.<br /><br /> Wartość domyślna to `EncryptAndSign`.|  
|sslProtocols|Wartość flagi wyliczenia SslProtocols określająca, które SslProtocols są obsługiwane. Wartość domyślna to protokołu Tls &#124; Tls11 &#124; Tls12.|  
|Właściwość policyEnforcement|To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.<br /><br /> 1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).<br />2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.<br />3.  Zawsze — zasady zawsze są wymuszane. Klienci, którzy nie obsługują ochrony rozszerzonej będzie mogło uwierzytelnić.|  
  
## <a name="clientcredentialtype-attribute"></a>właściwości ClientCredentialType o wartości atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Klient jest anonimowy. Wymaga certyfikatu usługi.|  
|Windows|Określa uwierzytelnianie systemu Windows dla klienta przy użyciu negocjacji SP (negocjacji protokołu Kerberos).|  
|certyfikat|Klient jest uwierzytelniany przy użyciu certyfikatu. Używa negocjacji w protokole SSL i wymaga certyfikatu dla usługi.|  
  
## <a name="protectionlevel-attribute"></a>Atrybut protectionLevel  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Brak ochrony.|  
|Zaloguj się|Komunikaty są podpisane.|  
|EncryptAndSign|— Liczba komunikatów są zaszyfrowana i podpisana.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Określa możliwości zabezpieczeń [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Uwagi  
 Należy użyć zabezpieczeń transportu, integralności i poufności komunikatu protokołu SOAP i do wzajemnego uwierzytelniania. Zaznaczenie tego trybu zabezpieczeń dla powiązania kanału stosu jest konfigurowana przy użyciu bezpiecznego transportu i wiadomości SOAP są zabezpieczone za pomocą zabezpieczeń transportu, takie jak Windows (Negotiate) lub protokołu SSL za pośrednictwem protokołu TCP.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.TcpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez System](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
