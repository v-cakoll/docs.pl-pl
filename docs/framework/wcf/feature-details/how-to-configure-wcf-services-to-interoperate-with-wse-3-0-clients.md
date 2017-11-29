---
title: "Instrukcje: Konfigurowanie usług WCF pod kątem współdziałania z klientami programu WSE 3.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 099fb059e375e0e76cffb5389191011d866b2d8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Instrukcje: Konfigurowanie usług WCF pod kątem współdziałania z klientami programu WSE 3.0
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]usługi są zgodne poziom danych przesyłanych w sieci z 3.0 rozszerzenia usługi sieci Web dla klientów programu Microsoft .NET (WSE) podczas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi są skonfigurowane do korzystania z sierpnia 2004 wersja specyfikacji WS-Addressing.  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Aby włączyć usługi WCF na potrzeby współdziałania z klientami programu WSE 3.0  
  
1.  Definiowanie niestandardowego powiązania dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.  
  
     Aby określić, czy wersja sierpnia 2004 specyfikacji WS-Addressing jest używany przez kodowania wiadomości, można utworzyć niestandardowego powiązania.  
  
    1.  Dodaj element podrzędny [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji usługi.  
  
    2.  Określ nazwę powiązania, dodając [ \<powiązania >](../../../../docs/framework/misc/binding.md) do [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) i ustawienie `name` atrybutu.  
  
    3.  Określ tryb uwierzytelniania i wersję specyfikacji WS-Security, które są używane do zabezpieczania komunikatów, które są zgodne z programu WSE 3.0, dodając element podrzędny [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) do [ \<powiązanie >](../../../../docs/framework/misc/binding.md).  
  
         Aby skonfigurować tryb uwierzytelniania, ustawić `authenicationMode` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Tryb uwierzytelniania jest w przybliżeniu do potwierdzenia zabezpieczeń gotowe, WSE 3.0. Poniższa tabela mapuje tryby uwierzytelniania w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do potwierdzenia zabezpieczeń gotowe w WSE 3.0.  
  
        |Tryb uwierzytelniania usługi WCF|Potwierdzenie gotowe zabezpieczeń programu WSE 3.0|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         \*Jeden z podstawowe różnice między `mutualCertificate10Security` i `mutualCertificate11Security` potwierdzeń zabezpieczeń gotowe jest wersja specyfikacji WS-Security, która używa WSE do zabezpieczenia wiadomości SOAP. Aby uzyskać `mutualCertificate10Security`, używane WS-Security w wersji 1.0, 1.1 WS-Security jest stosowany dla `mutualCertificate11Security`. Aby uzyskać [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], wersja specyfikacji WS-Security jest określona w `messageSecurityVersion` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Wersja specyfikacji WS-Security, która służy do zabezpieczania SOAP komunikatów ustawia `messageSecurityVersion` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Współdziałanie z programu WSE 3.0, ustaw wartość `messageSecurityVersion` atrybutu <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.  
  
    4.  Określ, czy wersja sierpnia 2004 specyfikacji WS-Addressing jest używany przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przez dodanie [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) i ustaw `messageVersion` wartością w celu <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.  
  
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
 [Porady: dostosowywanie powiązania dostarczane przez System](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
