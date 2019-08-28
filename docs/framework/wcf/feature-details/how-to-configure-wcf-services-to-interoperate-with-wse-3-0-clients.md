---
title: 'Instrukcje: Konfigurowanie usług WCF pod kątem współdziałania z klientami programu WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 0349c9ba76b3f240bf98daa0e095b415bc98a87c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045938"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Instrukcje: Konfigurowanie usług WCF pod kątem współdziałania z klientami programu WSE 3.0

Usługi Windows Communication Foundation (WCF) są zgodne ze standardami usług sieci Web udoskonalenia 3,0 dla klientów Microsoft .NET (WSE), gdy usługi WCF są skonfigurowane do używania wersji 2004 z sierpnia do specyfikacji WS-Addressing.

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Aby umożliwić usłudze WCF współdziałanie z klientami WSE 3,0

1. Zdefiniuj niestandardowe powiązanie dla usługi WCF.

    Aby określić, że wersja z sierpnia 2004 specyfikacji WS-Addressing jest używana do kodowania komunikatów, należy utworzyć powiązanie niestandardowe.

    1. Dodaj podrzędny element [ \<CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) [ \<> do powiązań >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji usługi.

    2. Określ nazwę powiązania, dodając `name` [ \<powiązanie](../../../../docs/framework/misc/binding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) > do niestandardowego elementubinding > i ustawiając atrybut.

    3. Określ tryb uwierzytelniania i wersję specyfikacji WS-Security, które są używane do zabezpieczania komunikatów zgodnych z WSE 3,0, dodając podrzędną [ \<](../../../../docs/framework/misc/binding.md) [ \<> zabezpieczeń](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) do > powiązań.

        Aby ustawić tryb uwierzytelniania, ustaw `authenticationMode` atrybut [ \<> zabezpieczeń](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Tryb uwierzytelniania jest w przybliżeniu równy gotowe zabezpieczenia w WSE 3,0. W poniższej tabeli zawarto mapy trybów uwierzytelniania w programie WCF, aby gotowe potwierdzenia zabezpieczeń w WSE 3,0.

        |Tryb uwierzytelniania WCF|WSE 3,0 gotowe Security Assertion|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        \*Jedną z głównych różnic między `mutualCertificate10Security` gotoweem a `mutualCertificate11Security` potwierdzeniem zabezpieczeń jest wersja specyfikacji WS-Security, która WSE używa do zabezpieczania komunikatów protokołu SOAP. W `mutualCertificate10Security`przypadku usługi WS-Security 1,0 używany jest protokół WS-Security 1,1 `mutualCertificate11Security`. W przypadku programu WCF wersja specyfikacji WS-Security jest określona w `messageSecurityVersion` atrybucie [ \<> zabezpieczeń](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).

        Aby ustawić wersję specyfikacji WS-Security, która jest używana do zabezpieczania komunikatów protokołu SOAP, ustaw `messageSecurityVersion` atrybut [ \<> zabezpieczeń](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Aby współdziałać z WSE 3,0, ustaw wartość `messageSecurityVersion` atrybutu na. <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>

    4. Określ, że wersja z sierpnia 2004 specyfikacji WS-Addressing jest używana przez funkcję WCF przez dodanie [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) i ustaw `messageVersion` wartość <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>na.

        > [!NOTE]
        > W przypadku korzystania z protokołu SOAP 1,2 należy ustawić `messageVersion` atrybut na <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.

2. Określ, że usługa używa niestandardowego powiązania.

    1. Ustaw atrybut elementu > `customBinding`punktukońcowegona. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) `binding`

    2. `bindingConfiguration` Ustaw atrybut`name` [ elementu\<> punktu końcowego](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) na [wartość określoną w atrybucie > powiązaniadlaniestandardowegopowiązania.\<](../../../../docs/framework/misc/binding.md)

## <a name="example"></a>Przykład

Poniższy przykład kodu określa, że `Service.HelloWorldService` używa niestandardowego powiązania do współpracy z klientami z systemem WSE 3,0. Niestandardowe powiązanie określa, że w sierpniu 2004 wersji WS-Addressing i WS-Security 1,1 zestawu specyfikacji są używane do kodowania komunikatów wymienianych. Komunikaty są zabezpieczane przy użyciu <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> trybu uwierzytelniania.

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

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dostosowywanie podanego przez system powiązania](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
