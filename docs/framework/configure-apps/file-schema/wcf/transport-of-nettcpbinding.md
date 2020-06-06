---
title: <transport> dla <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 4ef08ad73a03dea21d27217364a7bacb46a3848e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735934"
---
# <a name="transport-of-nettcpbinding"></a>\<transport> dla \<netTcpBinding>
Definiuje typ wymagań dotyczących zabezpieczeń na poziomie komunikatów dla punktu końcowego skonfigurowanego przy użyciu [\<netTcpBinding>](nettcpbinding.md) .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
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
|Powiązania ClientCredentialType|Opcjonalny. Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta przy użyciu zabezpieczeń transportu.<br /><br /> — Wartość domyślna to `Windows` .<br />-Ten atrybut jest typu <xref:System.ServiceModel.TcpClientCredentialType> .|  
|protectionLevel|Opcjonalny. Definiuje zabezpieczenia na poziomie transportu TCP. Komunikaty podpisywania zmniejszają ryzyko naruszenia przez osobę trzecią komunikatu podczas jego przesyłania. Szyfrowanie zapewnia prywatność na poziomie danych podczas transportu.<br /><br /> Wartość domyślna to `EncryptAndSign`.|  
|SslProtocols określająca|Wartość flagi wyliczenia SslProtocols określająca, która określa, które SslProtocols określająca są obsługiwane. Wartość domyślna to TLS&#124;Tls11&#124;Tls12.|  
|Zasady PolicyEnforcement|To Wyliczenie określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> należy wymusić.<br /><br /> 1. nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).<br />2. WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.<br />3. zawsze — zasady są zawsze wymuszane. Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialtype — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Klient jest anonimowy. Wymaga to certyfikatu dla usługi.|  
|Windows|Określa uwierzytelnianie systemu Windows klienta przy użyciu negocjacji SP (negocjowanie protokołu Kerberos).|  
|Certyfikat|Klient jest uwierzytelniany przy użyciu certyfikatu. Powoduje to użycie negocjacji protokołu SSL i wymaga certyfikatu dla usługi.|  
  
## <a name="protectionlevel-attribute"></a>protectionLevel — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Brak ochrony.|  
|Znak|Komunikaty są podpisane.|  
|EncryptAndSign|— Komunikaty są szyfrowane i podpisane.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|Określa możliwości zabezpieczeń programu [\<netTcpBinding>](nettcpbinding.md) .|  
  
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
- [\<binding>](bindings.md)
