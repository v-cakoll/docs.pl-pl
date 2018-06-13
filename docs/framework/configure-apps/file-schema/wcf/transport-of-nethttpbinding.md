---
title: '&lt;transport&gt; w &lt;netHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 6603e590632f0bc21a2d98482d1f42f03bb9d9e7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750222"
---
# <a name="lttransportgt-of-ltnethttpbindinggt"></a>&lt;transport&gt; w &lt;netHttpBinding&gt;
Definiuje właściwości sterujące parametrami uwierzytelniania dla transportu HTTP.  
  
\<system.serviceModel>  
\<powiązania >  
\<netHttpBinding >  
\<Powiązanie >  
\<Zabezpieczenia >  
\<transport>  
  
## <a name="syntax"></a>Składnia  
  
```xml
<netHttpBinding>  
  <binding>  
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string">  
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"  
                                  protectionScenario="TransportSelected|TrustedProxy">  
          <customServiceNames></customServiceNames>  
        </extendedProtectionPolicy>  
      </transport>  
    </security>  
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|clientCredentialType|— Określa typ poświadczenia, które będą używane podczas uwierzytelniania klienta przy użyciu uwierzytelniania HTTP.  Wartość domyślna to `None`. Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.|  
|proxyCredentialType|— Określa typ poświadczenia, które będą używane podczas uwierzytelniania klienta z w obrębie domeny przy użyciu serwera proxy za pośrednictwem protokołu HTTP. Ten atrybut jest stosowane tylko wtedy, gdy `mode` atrybutu nadrzędnego `security` jest element `Transport` lub `TransportCredentialsOnly`. Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|obszar|Ciąg określający obszar, który jest używany przez schemat uwierzytelniania HTTP dla uwierzytelniania podstawowego lub szyfrowanego. Wartość domyślna to ciąg pusty.|  
|policyEnforcement|To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.<br /><br /> 1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).<br />2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.<br />3.  Zawsze — zasady zawsze są wymuszane. Klienci, którzy nie obsługują ochrony rozszerzonej będzie mogło uwierzytelnić.|  
|protectionScenario|To wyliczenie Określa scenariusz ochrony wymuszany przez zasady.|  
  
## <a name="clientcredentialtype-attribute"></a>właściwości ClientCredentialType o wartości atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Komunikaty nie są już zabezpieczone podczas transferu.|  
|Podstawowy|Określa uwierzytelnianie podstawowe.|  
|Skrót|Określa uwierzytelnianie szyfrowane.|  
|Uwierzytelnianie NTLM|Określa uwierzytelniania NTLM, jeśli to możliwe, a w przypadku niepowodzenia uwierzytelniania systemu Windows.|  
|Windows|Określa zintegrowane uwierzytelnianie systemu Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|— Liczba komunikatów nie są już zabezpieczone podczas transferu.|  
|Podstawowy|Określa uwierzytelnianie podstawowe, zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Basic i uwierzytelniania szyfrowanego.|  
|Skrót|Określa uwierzytelnianie szyfrowane zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Basic i uwierzytelniania szyfrowanego.|  
|Uwierzytelnianie NTLM|Określa uwierzytelniania NTLM, jeśli to możliwe, a w przypadku niepowodzenia uwierzytelniania systemu Windows.|  
|Windows|Określa zintegrowane uwierzytelnianie systemu Windows.|  
|certyfikat|Wykonuje uwierzytelnianie klienta przy użyciu certyfikatu. Ta opcja działa tylko wtedy, gdy `Mode` atrybutu nadrzędnego `security` element ma ustawioną wartość transportu i nie będzie działać, jeśli jest ustawiona wartość TransportCredentialOnly.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|Definiuje funkcje zabezpieczeń dla [ \<netHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie zabezpieczenia transportowe protokołu SSL z powiązaniem podstawowe. Domyślnie podstawowe wiązanie obsługuje komunikację HTTP.  
  
```xml
<system.serviceModel>  
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="netHttpBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
    <netHttpBinding>  
      <!-- Configure basicHttpBinding with Transport security -- >  
      <!-- mode and clientCredentialType set to None.-->  
      <binding name="Binding1">  
        <security mode="Transport">  
          <transport clientCredentialType="None"  
                     proxyCredentialType="None">  
            <extendedProtectionPolicy policyEnforcement="WhenSupported"  
                                      protectionScenario="TransportSelected">  
              <customServiceNames></customServiceNames>  
            </extendedProtectionPolicy>
          </transport> 
        </security>  
      </binding>  
    </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport><xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
