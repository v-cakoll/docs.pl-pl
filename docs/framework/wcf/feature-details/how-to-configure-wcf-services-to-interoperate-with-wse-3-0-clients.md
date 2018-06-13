---
title: 'Instrukcje: Konfigurowanie usług WCF pod kątem współdziałania z klientami programu WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 174ecd279f9380136532ce0d5105b7a71b6d88da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495112"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Instrukcje: Konfigurowanie usług WCF pod kątem współdziałania z klientami programu WSE 3.0
Usługi Windows Communication Foundation (WCF) są zgodne poziom danych przesyłanych w sieci z 3.0 rozszerzenia usługi sieci Web dla klientów programu Microsoft .NET (WSE) po skonfigurowaniu usługi WCF do użycia wersja sierpnia 2004 specyfikacji WS-Addressing.  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Aby włączyć usługi WCF na potrzeby współdziałania z klientami programu WSE 3.0  
  
1.  Definiowanie niestandardowego powiązania dla usługi WCF.  
  
     Aby określić, czy wersja sierpnia 2004 specyfikacji WS-Addressing jest używany przez kodowania wiadomości, można utworzyć niestandardowego powiązania.  
  
    1.  Dodaj element podrzędny [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji usługi.  
  
    2.  Określ nazwę powiązania, dodając [ \<powiązania >](../../../../docs/framework/misc/binding.md) do [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) i ustawienie `name` atrybutu.  
  
    3.  Określ tryb uwierzytelniania i wersję specyfikacji WS-Security, które są używane do zabezpieczania komunikatów, które są zgodne z programu WSE 3.0, dodając element podrzędny [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) do [ \<powiązanie >](../../../../docs/framework/misc/binding.md).  
  
         Aby skonfigurować tryb uwierzytelniania, ustawić `authenicationMode` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Tryb uwierzytelniania jest w przybliżeniu do potwierdzenia zabezpieczeń gotowe, WSE 3.0. Poniższa tabela mapuje tryby uwierzytelniania w programie WCF potwierdzenia zabezpieczeń gotowe w WSE 3.0.  
  
        |Tryb uwierzytelniania usługi WCF|Potwierdzenie gotowe zabezpieczeń programu WSE 3.0|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         \* Jeden z podstawowe różnice między `mutualCertificate10Security` i `mutualCertificate11Security` potwierdzeń zabezpieczeń gotowe jest wersja specyfikacji WS-Security, która używa WSE do zabezpieczenia wiadomości SOAP. Aby uzyskać `mutualCertificate10Security`, używane WS-Security w wersji 1.0, 1.1 WS-Security jest stosowany dla `mutualCertificate11Security`. Dla usługi WCF, wersja specyfikacji WS-Security jest określona w `messageSecurityVersion` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Wersja specyfikacji WS-Security, która służy do zabezpieczania SOAP komunikatów ustawia `messageSecurityVersion` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Współdziałanie z programu WSE 3.0, ustaw wartość `messageSecurityVersion` atrybutu <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.  
  
    4.  Określ, czy sierpnia 2004 wersja specyfikacji WS-Addressing jest używany przez usługi WCF, dodając [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) i ustaw `messageVersion` wartością w celu <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.  
  
        > [!NOTE]
        >  Korzystając z protokołu SOAP 1.2, należy ustawić `messageVersion` atrybutu <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.  
  
2.  Określ, że usługa używa niestandardowego powiązania.  
  
    1.  Ustaw `binding` atrybutu [ \<punktu końcowego >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu `customBinding`.  
  
    2.  Ustaw `bindingConfiguration` atrybutu [ \<punktu końcowego >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu do wartości określonej w `name` atrybutu [ \<powiązania >](../../../../docs/framework/misc/binding.md) niestandardowe wiązanie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu Określa, że `Service.HelloWorldService` używa powiązania niestandardowego na potrzeby współdziałania z klientami programu WSE 3.0. Niestandardowego powiązania Określa, że wersja sierpnia 2004 WS-Addressing i zestaw 1.1 WS-Security specyfikacji do kodowania wymiana wiadomości. Komunikaty są chronione przy użyciu <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> tryb uwierzytelniania.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
        behaviorConfiguration="ServiceBehavior"   
        name="Service.HelloWorldService">  
        <endpoint binding="customBinding" address=""  
          bindingConfiguration="ServiceBinding"  
          contract="Service.IHelloWorld"></endpoint>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="ServiceBinding">  
          <security authenticationMode="AnonymousForCertificate"  
                  messageProtectionOrder="SignBeforeEncrypt"  
                  messageSecurityVersion="WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10"  
                  requireDerivedKeys="false">  
          </security>  
          <textMessageEncoding messageVersion ="Soap11WSAddressingAugust2004"></textMessageEncoding>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <behavior name="ServiceBehavior" returnUnknownExceptionsAsFaults="true">  
        <serviceCredentials>  
          <serviceCertificate findValue="CN=WCFQuickstartServer" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName"/>  
        </serviceCredentials>  
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: dostosowywanie powiązania udostępnionego przez system](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
