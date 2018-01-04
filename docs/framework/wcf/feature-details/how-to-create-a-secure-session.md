---
title: 'Instrukcje: Tworzenie bezpiecznej sesji'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: cd4f91ef5389dd4b8ecb63c1148d3a86918f2d10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="2a914-102">Instrukcje: Tworzenie bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="2a914-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="2a914-103">Z wyjątkiem produktów [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) powiązanie, powiązania dostarczane przez system w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] automatycznie użyj bezpiecznych sesji po włączeniu zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2a914-103">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="2a914-104">Domyślnie bezpiecznej sesji po serwera sieci Web, który zostanie odtworzony.</span><span class="sxs-lookup"><span data-stu-id="2a914-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="2a914-105">Podczas ustanawiania sesji bezpiecznych, klient i usługa pamięci podręcznej klucza, który jest skojarzony z bezpieczną sesję.</span><span class="sxs-lookup"><span data-stu-id="2a914-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="2a914-106">Jak komunikaty są wymieniane, są przekazywane tylko identyfikator, aby klucz pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="2a914-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="2a914-107">Jeśli serwer sieci Web zostanie odtworzony, pamięci podręcznej odtworzeniem również, tak, aby serwer sieci Web nie może pobrać klucz pamięci podręcznej dla identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="2a914-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="2a914-108">W takim przypadku jest zwracany wyjątek powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="2a914-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="2a914-109">Serwer sieci Web odtwarzane przełączniki bezpiecznych sesji, które używają token kontekstu zabezpieczeń stanową (SCT).</span><span class="sxs-lookup"><span data-stu-id="2a914-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="2a914-110">w ramach bezpiecznej sesji przy użyciu stanowe SCT zobacz [porady: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="2a914-110"> using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="2a914-111">Aby określić, że usługa używa bezpiecznych sesji przy użyciu jednego powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="2a914-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
-   <span data-ttu-id="2a914-112">Skonfiguruj usługę do używania wiązania dostarczane przez system, które obsługuje zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2a914-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="2a914-113">Z wyjątkiem produktów [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) powiązanie, gdy powiązania dostarczane przez system są skonfigurowane do korzystania z zabezpieczeń wiadomości [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatycznie używa bezpiecznych sesji.</span><span class="sxs-lookup"><span data-stu-id="2a914-113">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatically uses secure sessions.</span></span> <span data-ttu-id="2a914-114">W poniższej tabeli wymieniono powiązania dostarczane przez system obsługi zabezpieczeń komunikatów i określa, czy zabezpieczenia wiadomości są domyślnego mechanizmu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2a914-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="2a914-115">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="2a914-115">System-provided binding</span></span>|<span data-ttu-id="2a914-116">Element konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2a914-116">Configuration element</span></span>|<span data-ttu-id="2a914-117">Zabezpieczenia komunikatów na domyślnie</span><span class="sxs-lookup"><span data-stu-id="2a914-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[<span data-ttu-id="2a914-118">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="2a914-118">\<basicHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="2a914-119">Nie</span><span class="sxs-lookup"><span data-stu-id="2a914-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[<span data-ttu-id="2a914-120">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="2a914-120">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="2a914-121">Tak</span><span class="sxs-lookup"><span data-stu-id="2a914-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[<span data-ttu-id="2a914-122">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="2a914-122">\<wsDualHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="2a914-123">Tak</span><span class="sxs-lookup"><span data-stu-id="2a914-123">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[<span data-ttu-id="2a914-124">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="2a914-124">\<wsFederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="2a914-125">Tak</span><span class="sxs-lookup"><span data-stu-id="2a914-125">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[<span data-ttu-id="2a914-126">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="2a914-126">\<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="2a914-127">Nie</span><span class="sxs-lookup"><span data-stu-id="2a914-127">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[<span data-ttu-id="2a914-128">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="2a914-128">\<netMsmqBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="2a914-129">Nie</span><span class="sxs-lookup"><span data-stu-id="2a914-129">No</span></span>|  
  
     <span data-ttu-id="2a914-130">Poniższy przykład kodu wykorzystuje konfiguracji, aby określić powiązanie o nazwie `wsHttpBinding_Calculator` używającą [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), zabezpieczenia wiadomości i bezpieczne sesje.</span><span class="sxs-lookup"><span data-stu-id="2a914-130">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
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
  
     <span data-ttu-id="2a914-131">Poniższy przykład kodu Określa, że [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), zabezpieczenia wiadomości i bezpieczne sesje są używane do zabezpieczania `secureCalculator` usługi.</span><span class="sxs-lookup"><span data-stu-id="2a914-131">The following code example specifies that the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="2a914-132">Bezpieczne sesje, można wyłączyć dla [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) przez ustawienie `establishSecurityContext` atrybutu `false`.</span><span class="sxs-lookup"><span data-stu-id="2a914-132">Secure sessions can be turned off for the [<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="2a914-133">Dla innych dostarczane przez system powiązań można tylko wyłączyć bezpiecznej sesji przez utworzenie niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="2a914-133">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="2a914-134">Aby określić, że usługa używa bezpiecznych sesji przy użyciu wiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="2a914-134">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
-   <span data-ttu-id="2a914-135">Tworzenie niestandardowego powiązania, który określa, że wiadomości SOAP są chronione przez bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="2a914-135">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="2a914-136">Tworzenie niestandardowego powiązania, zobacz [porady: dostosowywanie powiązania System-Provided](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="2a914-136"> creating a custom binding, see [How to: Customize a System-Provided Binding](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="2a914-137">Poniższy przykład kodu wykorzystuje konfiguracji do określenia niestandardowego powiązania tej wiadomości za pomocą bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="2a914-137">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
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
  
     <span data-ttu-id="2a914-138">Poniższy przykład kodu tworzy niestandardowego powiązania, który używa <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> tryb uwierzytelniania do ładowania początkowego bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="2a914-138">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2a914-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a914-139">See Also</span></span>  
 [<span data-ttu-id="2a914-140">Omówienie powiązań WCF</span><span class="sxs-lookup"><span data-stu-id="2a914-140">WCF Bindings Overview</span></span>](../../../../docs/framework/wcf/bindings-overview.md)
