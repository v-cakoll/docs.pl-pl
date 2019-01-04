---
title: '&lt;transport&gt; w &lt;basicHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: 01fe2bc98326e3cef2b3df8bdf4aa03055df5e65
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54030337"
---
# <a name="lttransportgt-of-ltbasichttpbindinggt"></a>&lt;transport&gt; w &lt;basicHttpBinding&gt;
Definiuje właściwości sterujące parametrami uwierzytelniania dla protokołu HTTP.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<basicHttpBinding >  
\<Powiązanie >  
\<Zabezpieczenia >  
\<transport>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<basicHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
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
|clientCredentialType|-Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta przy użyciu uwierzytelniania HTTP.  Wartość domyślna to `None`. Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.|  
|proxyCredentialType|-Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta z w obrębie domeny przy użyciu serwera proxy za pośrednictwem protokołu HTTP. Ten atrybut jest stosowane tylko wtedy, gdy `mode` atrybutu elementu nadrzędnego `security` element jest `Transport` lub `TransportCredentialsOnly`. Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|obszar|Ciąg, który określa obszar, który jest używany przez schemat uwierzytelniania HTTP digest lub uwierzytelnianie podstawowe. Wartość domyślna to ciąg pusty.|  
|policyEnforcement|To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.<br /><br /> 1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrony rozszerzonej jest wyłączone).<br />2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.<br />3.  Zawsze — zasady zawsze są wymuszane. Klienci, którzy nie obsługują ochrony rozszerzonej zakończy się niepowodzeniem do uwierzytelniania.|  
|protectionScenario|To wyliczenie Określa scenariusz ochrony wymuszane przez zasady.|  
  
## <a name="clientcredentialtype-attribute"></a>właściwości ClientCredentialType o wartości atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Komunikaty nie są zabezpieczane podczas przesyłania.|  
|Podstawowy|Określa uwierzytelnianie podstawowe.|  
|Podsumowanie|Określa uwierzytelnianie szyfrowane.|  
|Uwierzytelnianie NTLM|Określa uwierzytelniania NTLM, jeśli jest to możliwe, a w przypadku niepowodzenia uwierzytelniania Windows.|  
|Windows|Określa, czy zintegrowane uwierzytelnianie Windows|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|— Liczba komunikatów nie są zabezpieczane podczas przesyłania.|  
|Podstawowy|Określa uwierzytelnianie podstawowe, zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Podstawowe i uwierzytelnianie szyfrowane.|  
|Podsumowanie|Określa uwierzytelniania szyfrowanego, zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Podstawowe i uwierzytelnianie szyfrowane.|  
|Uwierzytelnianie NTLM|Określa uwierzytelniania NTLM, jeśli jest to możliwe, a w przypadku niepowodzenia uwierzytelniania Windows.|  
|Windows|Określa, czy zintegrowane uwierzytelnianie Windows|  
|Certyfikat|Wykonuje uwierzytelnianie klienta przy użyciu certyfikatu. Ta opcja działa tylko wtedy, gdy `Mode` atrybutu elementu nadrzędnego `security` elementu jest ustawiona na Transport i nie będzie działać, jeśli jest ustawiona wartość TransportCredentialOnly.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Definiuje funkcje bezpieczeństwa umożliwiające [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje użycie protokołu SSL z zabezpieczeń transportu dla wiązania podstawowe. Domyślnie podstawowe powiązanie obsługuje komunikację HTTP.  
  
```xml  
<system.serviceModel>  
   <services>  
      <service   
          type="Microsoft.ServiceModel.Samples.CalculatorService"  
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
                       <extendedProtectionPolicy  
                          policyEnforcement="WhenSupported"  
                          protectionScenario="TransportSelected">  
                    <customServiceNames></customServiceNames>  
                       </extendedProtectionPolicy>  
               </security>  
           </binding>  
        </basicHttpBinding>  
    </bindings>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
