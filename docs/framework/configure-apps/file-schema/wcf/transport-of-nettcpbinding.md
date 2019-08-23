---
title: <transport> dla <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 265b68e058919d1d5c5f1dbcfb1419b57be9aeab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915548"
---
# <a name="transport-of-nettcpbinding"></a>\<Transport > \<NetTcpBinding >
Definiuje typ wymagań dotyczących zabezpieczeń na poziomie komunikatów dla punktu końcowego skonfigurowanego przy użyciu [ \<> NetTcpBinding](nettcpbinding.md).  
  
 \<system.ServiceModel>  
\<> powiązań  
\<netTcpBinding>  
\<> powiązania  
\<> zabezpieczeń  
\<transport>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|clientCredentialType|Opcjonalna. Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta przy użyciu zabezpieczeń transportu.<br /><br /> — Wartość domyślna to `Windows`.<br />-Ten atrybut jest typu <xref:System.ServiceModel.TcpClientCredentialType>.|  
|protectionLevel|Opcjonalny. Definiuje zabezpieczenia na poziomie transportu TCP. Komunikaty podpisywania zmniejszają ryzyko naruszenia przez osobę trzecią komunikatu podczas jego przesyłania. Szyfrowanie zapewnia prywatność na poziomie danych podczas transportu.<br /><br /> Wartość domyślna to `EncryptAndSign`.|  
|SslProtocols określająca|Wartość flagi wyliczenia SslProtocols określająca, która określa, które SslProtocols określająca są obsługiwane. Wartość domyślna to TLS&#124;Tls11&#124;Tls12.|  
|policyEnforcement|To Wyliczenie określa, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> Kiedy należy wymusić.<br /><br /> 1.  Nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).<br />2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.<br />3.  Zawsze — zasady są zawsze wymuszane. Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialtype — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Klient jest anonimowy. Wymaga to certyfikatu dla usługi.|  
|Windows|Określa uwierzytelnianie systemu Windows klienta przy użyciu negocjacji SP (negocjowanie protokołu Kerberos).|  
|Certyfikatu|Klient jest uwierzytelniany przy użyciu certyfikatu. Powoduje to użycie negocjacji protokołu SSL i wymaga certyfikatu dla usługi.|  
  
## <a name="protectionlevel-attribute"></a>protectionLevel — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Brak ochrony.|  
|Zapis|Komunikaty są podpisane.|  
|EncryptAndSign|— Komunikaty są szyfrowane i podpisane.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> zabezpieczeń](security-of-nettcpbinding.md)|Określa możliwości [ \<zabezpieczeń > NetTcpBinding](nettcpbinding.md).|  
  
## <a name="remarks"></a>Uwagi  
 Zabezpieczenia transportu umożliwiają integralność i poufność komunikatu protokołu SOAP oraz uwierzytelnianie wzajemne. Jeśli w powiązaniu wybrano ten tryb zabezpieczeń, stos kanału zostanie skonfigurowany przy użyciu bezpiecznego transportu, a komunikaty protokołu SOAP są zabezpieczone za pomocą zabezpieczeń transportu, takich jak Windows (Negotiate) lub SSL przez TCP.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> powiązania](../../../misc/binding.md)
