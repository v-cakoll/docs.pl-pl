---
title: 'Instrukcje: Konfigurowanie usług WCF pod kątem współdziałania z klientami programu WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 8f4407f66095f97a213d6cd987b4bd9a3ed340fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699789"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="072d5-102">Instrukcje: Konfigurowanie usług WCF pod kątem współdziałania z klientami programu WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="072d5-102">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>
<span data-ttu-id="072d5-103">Usług Windows Communication Foundation (WCF) są zgodne protokół sieciowy niskiego poziomu z rozszerzeń usługi sieci Web w wersji 3.0 dla klientów programu Microsoft .NET (WSE), gdy usług WCF są skonfigurowane do korzystania z sierpnia 2004 wersję specyfikacji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="072d5-103">Windows Communication Foundation (WCF) services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when WCF services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="072d5-104">Aby włączyć usługi WCF do współdziałania z klientami programu WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="072d5-104">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>  
  
1. <span data-ttu-id="072d5-105">Definiowanie niestandardowego powiązania dla usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="072d5-105">Define a custom binding for the WCF service.</span></span>  
  
     <span data-ttu-id="072d5-106">Aby określić, że wersja sierpnia 2004 specyfikacji WS-Addressing służy do kodowania wiadomości, można utworzyć niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="072d5-106">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>  
  
    1. <span data-ttu-id="072d5-107">Dodaj element podrzędny [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="072d5-107">Add a child [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>  
  
    2. <span data-ttu-id="072d5-108">Określ nazwę powiązania, dodając [ \<powiązania >](../../../../docs/framework/misc/binding.md) do [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) i ustawienie `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="072d5-108">Specify a name for the binding, by adding a [\<binding>](../../../../docs/framework/misc/binding.md) to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>  
  
    3. <span data-ttu-id="072d5-109">Określ tryb uwierzytelniania i wersję specyfikacji WS-Security, które są używane do zabezpieczenia wiadomości, które są zgodne z usługami WSE 3.0, dodając element podrzędny [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) do [ \<powiązanie >](../../../../docs/framework/misc/binding.md).</span><span class="sxs-lookup"><span data-stu-id="072d5-109">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../../../docs/framework/misc/binding.md).</span></span>  
  
         <span data-ttu-id="072d5-110">Aby ustawić tryb uwierzytelniania, należy ustawić `authenicationMode` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="072d5-110">To set the authentication mode, set the `authenicationMode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="072d5-111">Tryb uwierzytelniania jest w przybliżeniu do asercję gotowej do użycia zabezpieczeń programu WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="072d5-111">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="072d5-112">Poniższa tabela zawiera mapowanie tryby uwierzytelniania w usłudze WCF do potwierdzenia zabezpieczeń gotowej do użycia w programu WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="072d5-112">The following table maps authentication modes in WCF to turnkey security assertions in WSE 3.0.</span></span>  
  
        |<span data-ttu-id="072d5-113">Tryb uwierzytelniania programu WCF</span><span class="sxs-lookup"><span data-stu-id="072d5-113">WCF Authentication Mode</span></span>|<span data-ttu-id="072d5-114">Potwierdzenie zabezpieczeń gotowej do użycia programu WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="072d5-114">WSE 3.0 turnkey security assertion</span></span>|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         <span data-ttu-id="072d5-115">\* Jednym z podstawowe różnice między `mutualCertificate10Security` i `mutualCertificate11Security` potwierdzenia gotowej do użycia zabezpieczeń stanowi wersję specyfikacji WS-Security, która korzysta z programu WSE zabezpieczyć komunikaty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="072d5-115">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="072d5-116">Aby uzyskać `mutualCertificate10Security`, używane WS-Security w wersji 1.0, 1.1 WS-Security jest używane do `mutualCertificate11Security`.</span><span class="sxs-lookup"><span data-stu-id="072d5-116">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="072d5-117">Dla usługi WCF, wersję specyfikacji WS-Security jest określona w `messageSecurityVersion` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="072d5-117">For WCF, the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="072d5-118">Aby ustawić wersję specyfikacji WS-Security, która służy do zabezpieczania komunikaty protokołu SOAP, ustaw `messageSecurityVersion` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="072d5-118">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="072d5-119">Pod kątem współdziałania z usługami WSE 3.0, należy ustawić wartość `messageSecurityVersion` atrybutu <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span><span class="sxs-lookup"><span data-stu-id="072d5-119">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>  
  
    4. <span data-ttu-id="072d5-120">Określ, czy sierpnia 2004 wersję specyfikacji WS-Addressing jest używany przez usługę WCF, dodając [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) i ustaw `messageVersion` wartością w celu <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="072d5-120">Specify that the August 2004 version of the WS-Addressing specification is used by WCF by adding a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="072d5-121">Korzystając z protokołu SOAP 1.2, należy ustawić `messageVersion` atrybutu <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="072d5-121">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>  
  
2. <span data-ttu-id="072d5-122">Określ, czy usługa korzysta z niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="072d5-122">Specify that the service uses the custom binding.</span></span>  
  
    1. <span data-ttu-id="072d5-123">Ustaw `binding` atrybutu [ \<punktu końcowego >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu `customBinding`.</span><span class="sxs-lookup"><span data-stu-id="072d5-123">Set the `binding` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>  
  
    2. <span data-ttu-id="072d5-124">Ustaw `bindingConfiguration` atrybutu [ \<punktu końcowego >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element na wartość określoną w `name` atrybutu [ \<powiązania >](../../../../docs/framework/misc/binding.md) niestandardowe wiązanie.</span><span class="sxs-lookup"><span data-stu-id="072d5-124">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) for the custom binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="072d5-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="072d5-125">Example</span></span>  
 <span data-ttu-id="072d5-126">Poniższy przykład kodu Określa, że `Service.HelloWorldService` używa niestandardowego powiązania pod kątem współdziałania z klientami programu WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="072d5-126">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="072d5-127">Powiązania niestandardowego Określa wersję sierpnia 2004 WS-Addressing i zestaw 1.1 WS-Security specyfikacji służą do zakodowania wymiana wiadomości.</span><span class="sxs-lookup"><span data-stu-id="072d5-127">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="072d5-128">Komunikaty są chronione przy użyciu <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> tryb uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="072d5-128">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="072d5-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="072d5-129">See also</span></span>

- [<span data-ttu-id="072d5-130">Instrukcje: Dostosuj powiązania dostarczane przez System</span><span class="sxs-lookup"><span data-stu-id="072d5-130">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
