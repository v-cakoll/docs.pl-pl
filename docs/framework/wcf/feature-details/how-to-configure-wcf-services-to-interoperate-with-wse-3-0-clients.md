---
title: 'Instrukcje: Konfigurowanie usług WCF pod kątem współdziałania z klientami programu WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: bd9f2bec94ca45f76590f64366428a00edd5d6ea
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141744"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Instrukcje: Konfigurowanie usług WCF pod kątem współdziałania z klientami programu WSE 3.0

Usługi Windows Communication Foundation (WCF) są zgodne ze standardami usług sieci Web udoskonalenia 3,0 dla klientów Microsoft .NET (WSE), gdy usługi WCF są skonfigurowane do używania wersji 2004 z sierpnia do specyfikacji WS-Addressing.

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Aby umożliwić usłudze WCF współdziałanie z klientami WSE 3,0

1. Zdefiniuj niestandardowe powiązanie dla usługi WCF.

    Aby określić, że wersja z sierpnia 2004 specyfikacji WS-Addressing jest używana do kodowania komunikatów, należy utworzyć powiązanie niestandardowe.

    1. Dodaj podrzędną [\<niestandardowybinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do [\<powiązań >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji usługi.

    2. Określ nazwę dla powiązania przez dodanie [\<powiązania >](../../configure-apps/file-schema/wcf/bindings.md) do [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) i ustawienie atrybutu `name`.

    3. Określ tryb uwierzytelniania i wersję specyfikacji WS-Security, które są używane do zabezpieczania komunikatów zgodnych z WSE 3,0, dodając podrzędny [> zabezpieczeń\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) do [> powiązań\<](../../configure-apps/file-schema/wcf/bindings.md).

        Aby ustawić tryb uwierzytelniania, należy ustawić `authenticationMode` atrybutu [\<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Tryb uwierzytelniania jest w przybliżeniu równy gotowe zabezpieczenia w WSE 3,0. W poniższej tabeli zawarto mapy trybów uwierzytelniania w programie WCF, aby gotowe potwierdzenia zabezpieczeń w WSE 3,0.

        |Tryb uwierzytelniania WCF|WSE 3,0 gotowe Security Assertion|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        \* jedną z głównych różnic między `mutualCertificate10Security` i `mutualCertificate11Security` zatwierdzeń zabezpieczeń gotowe jest wersja specyfikacji WS-Security, która WSE używa do zabezpieczania komunikatów protokołu SOAP. W przypadku `mutualCertificate10Security`używany jest protokół WS-Security 1,0, a Usługa WS-Security 1,1 jest używana do `mutualCertificate11Security`. W przypadku programu WCF wersja specyfikacji WS-Security jest określona w atrybucie `messageSecurityVersion` [\<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).

        Aby ustawić wersję specyfikacji WS-Security, która jest używana do zabezpieczania komunikatów protokołu SOAP, należy ustawić atrybut `messageSecurityVersion` [\<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Aby współdziałać z WSE 3,0, ustaw wartość atrybutu `messageSecurityVersion` na <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.

    4. Określ, że wersja 2004 protokołu WS-Addressing z sierpnia jest używana przez program WCF poprzez dodanie [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) i ustaw `messageVersion` na jego wartość na <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.

        > [!NOTE]
        > Jeśli używasz protokołu SOAP 1,2, ustaw atrybut `messageVersion` na <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.

2. Określ, że usługa używa niestandardowego powiązania.

    1. Ustaw atrybut `binding` elementu [\<punktu końcowego >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) na `customBinding`.

    2. Ustaw atrybut `bindingConfiguration` elementu [\<endpoint >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) na wartość określoną w atrybucie `name` [powiązania\<](../../configure-apps/file-schema/wcf/bindings.md) dla niestandardowego powiązania.

## <a name="example"></a>Przykład

Poniższy przykład kodu określa, że `Service.HelloWorldService` używa niestandardowego powiązania do współpracy z klientami z systemem WSE 3,0. Niestandardowe powiązanie określa, że w sierpniu 2004 wersji WS-Addressing i WS-Security 1,1 zestawu specyfikacji są używane do kodowania komunikatów wymienianych. Komunikaty są zabezpieczane przy użyciu trybu uwierzytelniania <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>.

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

- [Instrukcje: dostosowywanie powiązania udostępnionego przez system](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
