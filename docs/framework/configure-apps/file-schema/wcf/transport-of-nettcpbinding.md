---
title: '&lt;transport&gt; w &lt;netTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 8416701ce4e787a49ee0a4bdd4829c6592cde94c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147333"
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a>&lt;transport&gt; w &lt;netTcpBinding&gt;
Określa typ zabezpieczenia na poziomie wiadomości dotyczące punkty końcowe skonfigurowane za pomocą [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netTcpBinding>  
\<Powiązanie >  
\<Zabezpieczenia >  
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
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|clientCredentialType|Opcjonalna. Określa typ poświadczeń ma być używany podczas uwierzytelniania klientów za pomocą zabezpieczeń transportu.<br /><br /> — Wartość domyślna to `Windows`.<br />— Ten atrybut jest typu <xref:System.ServiceModel.TcpClientCredentialType>.|  
|protectionLevel|Opcjonalna. Definiuje zabezpieczenia na poziomie warstwy transportowej TCP. Podpisywania wiadomości zmniejsza ryzyko związane z innej naruszeniu komunikat, gdy są przesyłane. Szyfrowanie zapewnia ochronę poufności poziom danych, podczas transportu.<br /><br /> Wartość domyślna to `EncryptAndSign`.|  
|sslProtocols|Wartość flagi wyliczenia SslProtocols określająca SslProtocols, które są obsługiwane. Wartość domyślna to protokołu Tls&#124;Tls11&#124;Tls12.|  
|policyEnforcement|To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.<br /><br /> 1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrony rozszerzonej jest wyłączone).<br />2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.<br />3.  Zawsze — zasady zawsze są wymuszane. Klienci, którzy nie obsługują ochrony rozszerzonej zakończy się niepowodzeniem do uwierzytelniania.|  
  
## <a name="clientcredentialtype-attribute"></a>właściwości ClientCredentialType o wartości atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Klient jest anonimowy. Wymaga certyfikatu usługi.|  
|Windows|Określa Windows uwierzytelniania klienta przy użyciu negocjacji SP (negocjacji protokołu Kerberos).|  
|Certyfikat|Klient jest uwierzytelniany przy użyciu certyfikatu. Ten wymaga negocjacji w protokole SSL i wymaga certyfikatu usługi.|  
  
## <a name="protectionlevel-attribute"></a>protectionLevel atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Brak ochrony.|  
|Logowanie|Komunikaty są podpisane.|  
|EncryptAndSign|— Liczba komunikatów jest zaszyfrowany i podpisany.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Określa możliwości zabezpieczeń [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą zabezpieczeń transportu integralności i poufności komunikatu protokołu SOAP, jak i do wzajemnego uwierzytelniania. Zaznaczenie tego trybu zabezpieczeń w powiązaniu ze stosu kanał jest skonfigurowany przy użyciu bezpiecznym transportem i komunikaty protokołu SOAP są zabezpieczone za pomocą zabezpieczeń transportu, takich jak Windows (Negotiate) lub protokołu SSL, za pośrednictwem protokołu TCP.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.TcpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
