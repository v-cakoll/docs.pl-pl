---
title: <transport> dla <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: c563339e4f854cc4e60f92dd5b8c0b39112dc000
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736121"
---
# <a name="transport-of-basichttpbinding"></a>\<Transport > \<basicHttpBinding >
Definiuje właściwości kontrolujące parametry uwierzytelniania dla transportu HTTP.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<BasicHttpBinding**](basichttpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpieczeń**](security-of-basichttpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transport >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<basicHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="String">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Powiązania ClientCredentialType|-Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta przy użyciu uwierzytelniania HTTP.  Wartość domyślna to `None`. Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.|  
|proxyCredentialType|-Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta w domenie przy użyciu serwera proxy za pośrednictwem protokołu HTTP. Ten atrybut jest stosowany tylko wtedy, gdy atrybut `mode` elementu nadrzędnego `security` jest `Transport` lub `TransportCredentialsOnly`. Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|obszarów|Ciąg określający obszar, który jest używany przez schemat uwierzytelniania HTTP na potrzeby uwierzytelniania szyfrowanego lub podstawowego. Wartość domyślna to pusty ciąg.|  
|Zasady PolicyEnforcement|To Wyliczenie określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> należy wymusić.<br /><br /> 1. nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).<br />2. WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.<br />3. zawsze — zasady są zawsze wymuszane. Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.|  
|protectionScenario|To Wyliczenie określa scenariusz ochrony wymuszany przez zasady.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialtype — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Komunikaty nie są zabezpieczane podczas transferu.|  
|Podstawowy|Określa podstawowe uwierzytelnianie.|  
|szyfrowane|Określa uwierzytelnianie szyfrowane.|  
|NTLM|Określa uwierzytelnianie NTLM, jeśli jest to możliwe, a uwierzytelnianie systemu Windows kończy się niepowodzeniem.|  
|Windows|Określa zintegrowane uwierzytelnianie systemu Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|-Komunikaty nie są zabezpieczane podczas transferu.|  
|Podstawowy|Określa uwierzytelnianie podstawowe zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: uwierzytelnianie podstawowe i szyfrowane.|  
|szyfrowane|Określa uwierzytelnianie szyfrowane zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: uwierzytelnianie podstawowe i szyfrowane.|  
|NTLM|Określa uwierzytelnianie NTLM, jeśli jest to możliwe, a uwierzytelnianie systemu Windows kończy się niepowodzeniem.|  
|Windows|Określa zintegrowane uwierzytelnianie systemu Windows.|  
|Certyfikatu|Wykonuje uwierzytelnianie klienta przy użyciu certyfikatu. Ta opcja działa tylko wtedy, gdy atrybut `Mode` nadrzędnego elementu `security` jest ustawiony na transport i nie będzie działać, jeśli zostanie ustawiony na wartość TransportCredentialOnly.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[> zabezpieczeń \<](security-of-basichttpbinding.md)|Definiuje możliwości zabezpieczeń dla [\<> BasicHttpBinding](basichttpbinding.md).|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje użycie zabezpieczeń transportu SSL z powiązaniem podstawowym. Domyślnie podstawowe powiązanie obsługuje komunikację HTTP.  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [> powiązań \<](bindings.md)
