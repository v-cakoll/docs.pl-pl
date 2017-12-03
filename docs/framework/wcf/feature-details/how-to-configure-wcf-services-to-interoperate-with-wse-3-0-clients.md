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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5589ad8e4193416738da98676551bbf82c128a79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="bae90-102">Instrukcje: Konfigurowanie usług WCF pod kątem współdziałania z klientami programu WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="bae90-102">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="bae90-103">usługi są zgodne poziom danych przesyłanych w sieci z 3.0 rozszerzenia usługi sieci Web dla klientów programu Microsoft .NET (WSE) podczas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi są skonfigurowane do korzystania z sierpnia 2004 wersja specyfikacji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="bae90-103"> services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="bae90-104">Aby włączyć usługi WCF na potrzeby współdziałania z klientami programu WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="bae90-104">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>  
  
1.  <span data-ttu-id="bae90-105">Definiowanie niestandardowego powiązania dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="bae90-105">Define a custom binding for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
     <span data-ttu-id="bae90-106">Aby określić, czy wersja sierpnia 2004 specyfikacji WS-Addressing jest używany przez kodowania wiadomości, można utworzyć niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="bae90-106">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>  
  
    1.  <span data-ttu-id="bae90-107">Dodaj element podrzędny [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="bae90-107">Add a child [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>  
  
    2.  <span data-ttu-id="bae90-108">Określ nazwę powiązania, dodając [ \<powiązania >](../../../../docs/framework/misc/binding.md) do [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) i ustawienie `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bae90-108">Specify a name for the binding, by adding a [\<binding>](../../../../docs/framework/misc/binding.md) to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>  
  
    3.  <span data-ttu-id="bae90-109">Określ tryb uwierzytelniania i wersję specyfikacji WS-Security, które są używane do zabezpieczania komunikatów, które są zgodne z programu WSE 3.0, dodając element podrzędny [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) do [ \<powiązanie >](../../../../docs/framework/misc/binding.md).</span><span class="sxs-lookup"><span data-stu-id="bae90-109">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../../../docs/framework/misc/binding.md).</span></span>  
  
         <span data-ttu-id="bae90-110">Aby skonfigurować tryb uwierzytelniania, ustawić `authenicationMode` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="bae90-110">To set the authentication mode, set the `authenicationMode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="bae90-111">Tryb uwierzytelniania jest w przybliżeniu do potwierdzenia zabezpieczeń gotowe, WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="bae90-111">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="bae90-112">Poniższa tabela mapuje tryby uwierzytelniania w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do potwierdzenia zabezpieczeń gotowe w WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="bae90-112">The following table maps authentication modes in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to turnkey security assertions in WSE 3.0.</span></span>  
  
        |<span data-ttu-id="bae90-113">Tryb uwierzytelniania usługi WCF</span><span class="sxs-lookup"><span data-stu-id="bae90-113">WCF Authentication Mode</span></span>|<span data-ttu-id="bae90-114">Potwierdzenie gotowe zabezpieczeń programu WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="bae90-114">WSE 3.0 turnkey security assertion</span></span>|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         <span data-ttu-id="bae90-115">\*Jeden z podstawowe różnice między `mutualCertificate10Security` i `mutualCertificate11Security` potwierdzeń zabezpieczeń gotowe jest wersja specyfikacji WS-Security, która używa WSE do zabezpieczenia wiadomości SOAP.</span><span class="sxs-lookup"><span data-stu-id="bae90-115">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="bae90-116">Aby uzyskać `mutualCertificate10Security`, używane WS-Security w wersji 1.0, 1.1 WS-Security jest stosowany dla `mutualCertificate11Security`.</span><span class="sxs-lookup"><span data-stu-id="bae90-116">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="bae90-117">Aby uzyskać [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], wersja specyfikacji WS-Security jest określona w `messageSecurityVersion` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="bae90-117">For [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="bae90-118">Wersja specyfikacji WS-Security, która służy do zabezpieczania SOAP komunikatów ustawia `messageSecurityVersion` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="bae90-118">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="bae90-119">Współdziałanie z programu WSE 3.0, ustaw wartość `messageSecurityVersion` atrybutu <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span><span class="sxs-lookup"><span data-stu-id="bae90-119">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>  
  
    4.  <span data-ttu-id="bae90-120">Określ, czy wersja sierpnia 2004 specyfikacji WS-Addressing jest używany przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przez dodanie [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) i ustaw `messageVersion` wartością w celu <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="bae90-120">Specify that the August 2004 version of the WS-Addressing specification is used by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by adding a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="bae90-121">Korzystając z protokołu SOAP 1.2, należy ustawić `messageVersion` atrybutu <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="bae90-121">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>  
  
2.  <span data-ttu-id="bae90-122">Określ, że usługa używa niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="bae90-122">Specify that the service uses the custom binding.</span></span>  
  
    1.  <span data-ttu-id="bae90-123">Ustaw `binding` atrybutu [ \<punktu końcowego >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu `customBinding`.</span><span class="sxs-lookup"><span data-stu-id="bae90-123">Set the `binding` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>  
  
    2.  <span data-ttu-id="bae90-124">Ustaw `bindingConfiguration` atrybutu [ \<punktu końcowego >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu do wartości określonej w `name` atrybutu [ \<powiązania >](../../../../docs/framework/misc/binding.md) niestandardowe wiązanie.</span><span class="sxs-lookup"><span data-stu-id="bae90-124">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) for the custom binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bae90-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="bae90-125">Example</span></span>  
 <span data-ttu-id="bae90-126">Poniższy przykład kodu Określa, że `Service.HelloWorldService` używa powiązania niestandardowego na potrzeby współdziałania z klientami programu WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="bae90-126">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="bae90-127">Niestandardowego powiązania Określa, że wersja sierpnia 2004 WS-Addressing i zestaw 1.1 WS-Security specyfikacji do kodowania wymiana wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bae90-127">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="bae90-128">Komunikaty są chronione przy użyciu <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> tryb uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="bae90-128">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bae90-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bae90-129">See Also</span></span>  
 [<span data-ttu-id="bae90-130">Porady: dostosowywanie powiązania dostarczane przez System</span><span class="sxs-lookup"><span data-stu-id="bae90-130">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
