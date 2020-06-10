---
title: 'Instrukcje: Konfigurowanie usług WCF pod kątem współdziałania z klientami programu WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 600b9c28d92f9e2b6e4d586b052cc5762d591521
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599064"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="13441-102">Instrukcje: Konfigurowanie usług WCF pod kątem współdziałania z klientami programu WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="13441-102">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>

<span data-ttu-id="13441-103">Usługi Windows Communication Foundation (WCF) są zgodne ze standardami usług sieci Web udoskonalenia 3,0 dla klientów Microsoft .NET (WSE), gdy usługi WCF są skonfigurowane do używania wersji 2004 z sierpnia do specyfikacji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="13441-103">Windows Communication Foundation (WCF) services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when WCF services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="13441-104">Aby umożliwić usłudze WCF współdziałanie z klientami WSE 3,0</span><span class="sxs-lookup"><span data-stu-id="13441-104">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>

1. <span data-ttu-id="13441-105">Zdefiniuj niestandardowe powiązanie dla usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="13441-105">Define a custom binding for the WCF service.</span></span>

    <span data-ttu-id="13441-106">Aby określić, że wersja z sierpnia 2004 specyfikacji WS-Addressing jest używana do kodowania komunikatów, należy utworzyć powiązanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="13441-106">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>

    1. <span data-ttu-id="13441-107">Dodaj element podrzędny [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) do [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="13441-107">Add a child [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>

    2. <span data-ttu-id="13441-108">Określ nazwę dla powiązania, dodając [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) do [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) i ustawiając `name` atrybut.</span><span class="sxs-lookup"><span data-stu-id="13441-108">Specify a name for the binding, by adding a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) to the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>

    3. <span data-ttu-id="13441-109">Określ tryb uwierzytelniania i wersję specyfikacji WS-Security, które są używane do zabezpieczania komunikatów zgodnych z WSE 3,0, dodając element podrzędny [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) do programu [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="13441-109">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md).</span></span>

        <span data-ttu-id="13441-110">Aby ustawić tryb uwierzytelniania, ustaw `authenticationMode` atrybut [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="13441-110">To set the authentication mode, set the `authenticationMode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="13441-111">Tryb uwierzytelniania jest w przybliżeniu równy gotowe zabezpieczenia w WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="13441-111">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="13441-112">W poniższej tabeli zawarto mapy trybów uwierzytelniania w programie WCF, aby gotowe potwierdzenia zabezpieczeń w WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="13441-112">The following table maps authentication modes in WCF to turnkey security assertions in WSE 3.0.</span></span>

        |<span data-ttu-id="13441-113">Tryb uwierzytelniania WCF</span><span class="sxs-lookup"><span data-stu-id="13441-113">WCF Authentication Mode</span></span>|<span data-ttu-id="13441-114">WSE 3,0 gotowe Security Assertion</span><span class="sxs-lookup"><span data-stu-id="13441-114">WSE 3.0 turnkey security assertion</span></span>|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        <span data-ttu-id="13441-115">\*Jedną z głównych różnic między `mutualCertificate10Security` `mutualCertificate11Security` gotoweem a potwierdzeniem zabezpieczeń jest wersja specyfikacji WS-Security, która WSE używa do zabezpieczania komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="13441-115">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="13441-116">W przypadku `mutualCertificate10Security` usługi WS-security 1,0 używany jest protokół WS-security 1,1 `mutualCertificate11Security` .</span><span class="sxs-lookup"><span data-stu-id="13441-116">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="13441-117">W przypadku programu WCF wersja specyfikacji WS-Security jest określona w `messageSecurityVersion` atrybucie [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="13441-117">For WCF, the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>

        <span data-ttu-id="13441-118">Aby ustawić wersję specyfikacji WS-Security, która jest używana do zabezpieczania komunikatów protokołu SOAP, ustaw `messageSecurityVersion` atrybut [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="13441-118">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="13441-119">Aby współdziałać z WSE 3,0, ustaw wartość `messageSecurityVersion` atrybutu na <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A> .</span><span class="sxs-lookup"><span data-stu-id="13441-119">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>

    4. <span data-ttu-id="13441-120">Określ, że wersja z sierpnia 2004 specyfikacji WS-Addressing jest używana przez funkcję WCF poprzez dodanie [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) i ustawienie `messageVersion` wartości do <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A> .</span><span class="sxs-lookup"><span data-stu-id="13441-120">Specify that the August 2004 version of the WS-Addressing specification is used by WCF by adding a [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>

        > [!NOTE]
        > <span data-ttu-id="13441-121">W przypadku korzystania z protokołu SOAP 1,2 należy ustawić `messageVersion` atrybut na <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A> .</span><span class="sxs-lookup"><span data-stu-id="13441-121">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>

2. <span data-ttu-id="13441-122">Określ, że usługa używa niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="13441-122">Specify that the service uses the custom binding.</span></span>

    1. <span data-ttu-id="13441-123">Ustaw `binding` atrybut [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) elementu na `customBinding` .</span><span class="sxs-lookup"><span data-stu-id="13441-123">Set the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>

    2. <span data-ttu-id="13441-124">Ustaw `bindingConfiguration` atrybut [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) elementu na wartość określoną w `name` atrybucie [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="13441-124">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) for the custom binding.</span></span>

## <a name="example"></a><span data-ttu-id="13441-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="13441-125">Example</span></span>

<span data-ttu-id="13441-126">Poniższy przykład kodu określa, że `Service.HelloWorldService` używa niestandardowego powiązania do współpracy z klientami z systemem WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="13441-126">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="13441-127">Niestandardowe powiązanie określa, że w sierpniu 2004 wersji WS-Addressing i WS-Security 1,1 zestawu specyfikacji są używane do kodowania komunikatów wymienianych.</span><span class="sxs-lookup"><span data-stu-id="13441-127">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="13441-128">Komunikaty są zabezpieczane przy użyciu <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> trybu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="13441-128">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="13441-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13441-129">See also</span></span>

- [<span data-ttu-id="13441-130">Instrukcje: dostosowywanie powiązania udostępnionego przez system</span><span class="sxs-lookup"><span data-stu-id="13441-130">How to: Customize a System-Provided Binding</span></span>](../extending/how-to-customize-a-system-provided-binding.md)
