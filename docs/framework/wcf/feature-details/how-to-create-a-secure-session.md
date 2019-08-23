---
title: 'Instrukcje: tworzenie bezpiecznej sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: bdb0f89b950d086e04cbb9d6da161bd315fc64b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934381"
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="bff97-102">Instrukcje: tworzenie bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="bff97-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="bff97-103">Z wyjątkiem [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) powiązania dostarczone przez system w Windows Communication Foundation (WCF) automatycznie używają bezpiecznych sesji, gdy włączono zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="bff97-103">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="bff97-104">Domyślnie bezpieczne sesje nie przeżyły serwera sieci Web, który jest odtwarzany ponownie.</span><span class="sxs-lookup"><span data-stu-id="bff97-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="bff97-105">Po ustanowieniu bezpiecznej sesji klient i usługa buforują klucz skojarzony z bezpieczną sesją.</span><span class="sxs-lookup"><span data-stu-id="bff97-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="bff97-106">Podczas wymiany komunikatów wymieniany jest tylko identyfikator klucza w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="bff97-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="bff97-107">Jeśli serwer sieci Web jest odtwarzany ponownie, pamięć podręczna jest również odtwarzana w taki sposób, że serwer sieci Web nie może pobrać klucza buforowanego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="bff97-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="bff97-108">W takim przypadku wyjątek jest zgłaszany z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="bff97-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="bff97-109">Bezpieczne sesje korzystające z tokenu stanowego kontekstu zabezpieczeń (SCT) mogą przetrwać serwer sieci Web, który jest odtwarzany.</span><span class="sxs-lookup"><span data-stu-id="bff97-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="bff97-110">Aby uzyskać więcej informacji na temat używania stanowego SCT w bezpiecznej sesji, [zobacz How to: Utwórz token kontekstu zabezpieczeń dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="bff97-110">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="bff97-111">Aby określić, że usługa używa zabezpieczonych sesji przy użyciu jednego z powiązań dostarczonych przez system</span><span class="sxs-lookup"><span data-stu-id="bff97-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
- <span data-ttu-id="bff97-112">Skonfiguruj usługę do korzystania z powiązania dostarczonego przez system, które obsługuje zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="bff97-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="bff97-113">Z wyjątkiem [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) , gdy powiązania dostarczone z systemem są skonfigurowane do korzystania z zabezpieczeń wiadomości, WCF automatycznie używa bezpiecznych sesji.</span><span class="sxs-lookup"><span data-stu-id="bff97-113">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="bff97-114">Poniższa tabela zawiera listę powiązań dostarczonych przez system, które obsługują zabezpieczenia komunikatów i czy zabezpieczenia komunikatów są domyślnym mechanizmem zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bff97-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="bff97-115">Powiązanie dostarczone przez system</span><span class="sxs-lookup"><span data-stu-id="bff97-115">System-provided binding</span></span>|<span data-ttu-id="bff97-116">Element konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bff97-116">Configuration element</span></span>|<span data-ttu-id="bff97-117">Zabezpieczenia komunikatów domyślnie włączone</span><span class="sxs-lookup"><span data-stu-id="bff97-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[<span data-ttu-id="bff97-118">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="bff97-118">\<basicHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="bff97-119">Nie</span><span class="sxs-lookup"><span data-stu-id="bff97-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[<span data-ttu-id="bff97-120">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="bff97-120">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="bff97-121">Tak</span><span class="sxs-lookup"><span data-stu-id="bff97-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[<span data-ttu-id="bff97-122">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="bff97-122">\<wsDualHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="bff97-123">Tak</span><span class="sxs-lookup"><span data-stu-id="bff97-123">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[<span data-ttu-id="bff97-124">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="bff97-124">\<wsFederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="bff97-125">Tak</span><span class="sxs-lookup"><span data-stu-id="bff97-125">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[<span data-ttu-id="bff97-126">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="bff97-126">\<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="bff97-127">Nie</span><span class="sxs-lookup"><span data-stu-id="bff97-127">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[<span data-ttu-id="bff97-128">\<> usługi Msmqbinding</span><span class="sxs-lookup"><span data-stu-id="bff97-128">\<netMsmqBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="bff97-129">Nie</span><span class="sxs-lookup"><span data-stu-id="bff97-129">No</span></span>|  
  
     <span data-ttu-id="bff97-130">Poniższy przykład kodu używa konfiguracji do określenia powiązania o nazwie `wsHttpBinding_Calculator` , który [ \<używa WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), zabezpieczeń komunikatów i zabezpieczonych sesji.</span><span class="sxs-lookup"><span data-stu-id="bff97-130">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
    ```xml  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="bff97-131">Poniższy przykład kodu określa, że [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), zabezpieczenia komunikatów i bezpieczne sesje są `secureCalculator` używane do zabezpieczenia usługi.</span><span class="sxs-lookup"><span data-stu-id="bff97-131">The following code example specifies that the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="bff97-132">Bezpieczne sesje można wyłączyć dla [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) przez ustawienie `establishSecurityContext` atrybutu na `false`.</span><span class="sxs-lookup"><span data-stu-id="bff97-132">Secure sessions can be turned off for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="bff97-133">W przypadku innych powiązań dostarczonych z systemem bezpieczne sesje można wyłączyć tylko przez utworzenie niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="bff97-133">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="bff97-134">Aby określić, że usługa używa zabezpieczonych sesji przy użyciu niestandardowego powiązania</span><span class="sxs-lookup"><span data-stu-id="bff97-134">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
- <span data-ttu-id="bff97-135">Utwórz niestandardowe powiązanie, które określa, że wiadomości protokołu SOAP są chronione przez bezpieczną sesję.</span><span class="sxs-lookup"><span data-stu-id="bff97-135">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="bff97-136">Aby uzyskać więcej informacji na temat tworzenia niestandardowego powiązania, [zobacz How to: Dostosuj powiązanie](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)dostarczone przez system.</span><span class="sxs-lookup"><span data-stu-id="bff97-136">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="bff97-137">Poniższy przykład kodu używa konfiguracji do określenia niestandardowego powiązania, które wiadomości używają bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="bff97-137">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
    ```xml  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="bff97-138">Poniższy przykład kodu tworzy niestandardowe powiązanie, które używa <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> trybu uwierzytelniania do uruchamiania bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="bff97-138">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="bff97-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bff97-139">See also</span></span>

- [<span data-ttu-id="bff97-140">Omówienie powiązań WCF</span><span class="sxs-lookup"><span data-stu-id="bff97-140">WCF Bindings Overview</span></span>](../../../../docs/framework/wcf/bindings-overview.md)
