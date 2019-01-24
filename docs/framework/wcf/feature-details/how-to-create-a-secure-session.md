---
title: 'Instrukcje: Tworzenie bezpiecznej sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: c2e2b34c1d1589f26f3aea80384b5a96f1c64fb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544721"
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="54431-102">Instrukcje: Tworzenie bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="54431-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="54431-103">Z wyjątkiem produktów [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) powiązania powiązania dostarczane przez system w Windows Communication Foundation (WCF) automatycznie używać bezpiecznych sesji po włączeniu zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="54431-103">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="54431-104">Domyślnie bezpiecznych sesji nie przeżywa serwera sieci Web, która zostanie odtworzona.</span><span class="sxs-lookup"><span data-stu-id="54431-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="54431-105">Podczas ustanawiania sesji bezpiecznego, klient i usługa pamięci podręcznej klucza, który jest skojarzony z bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="54431-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="54431-106">Ponieważ komunikaty są wymieniane, wymieniane są tylko identyfikator, aby klucz pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="54431-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="54431-107">Jeśli serwer sieci Web zostanie odtworzona, pamięć podręczna jest recyklingowi, taki sposób, że serwer sieci Web nie może pobrać klucza pamięci podręcznej dla identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="54431-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="54431-108">Jeśli tak się stanie, wyjątek jest generowany ponownie do klienta.</span><span class="sxs-lookup"><span data-stu-id="54431-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="54431-109">Bezpieczne sesje, które używają tokenu kontekstu zabezpieczeń stanową (SCT) może nie są unieważniane serwer sieci Web z odtwarzania.</span><span class="sxs-lookup"><span data-stu-id="54431-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="54431-110">Aby uzyskać więcej informacji na temat w ramach bezpiecznej sesji przy użyciu stanowych SCT zobacz [jak: Utwórz kontekst zabezpieczeń tokenu dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="54431-110">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="54431-111">Aby określić, że usługa używa bezpiecznej sesji przy użyciu jednej z powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="54431-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
-   <span data-ttu-id="54431-112">Skonfiguruj usługę do używania powiązania dostarczane przez system, które obsługuje zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="54431-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="54431-113">Z wyjątkiem produktów [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) powiązania, kiedy powiązania dostarczane przez system są skonfigurowane do używania zabezpieczeń wiadomości, WCF, automatycznie używa bezpiecznych sesji.</span><span class="sxs-lookup"><span data-stu-id="54431-113">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="54431-114">W poniższej tabeli wymieniono powiązania dostarczane przez system, które obsługują zabezpieczenia komunikatów i tego, czy zabezpieczenia wiadomości są domyślnego mechanizmu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="54431-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="54431-115">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="54431-115">System-provided binding</span></span>|<span data-ttu-id="54431-116">Element konfiguracji</span><span class="sxs-lookup"><span data-stu-id="54431-116">Configuration element</span></span>|<span data-ttu-id="54431-117">Zabezpieczenia komunikatów na domyślnie</span><span class="sxs-lookup"><span data-stu-id="54431-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[<span data-ttu-id="54431-118">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="54431-118">\<basicHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="54431-119">Nie</span><span class="sxs-lookup"><span data-stu-id="54431-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[<span data-ttu-id="54431-120">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="54431-120">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="54431-121">Tak</span><span class="sxs-lookup"><span data-stu-id="54431-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[<span data-ttu-id="54431-122">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="54431-122">\<wsDualHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="54431-123">Tak</span><span class="sxs-lookup"><span data-stu-id="54431-123">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[<span data-ttu-id="54431-124">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="54431-124">\<wsFederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="54431-125">Tak</span><span class="sxs-lookup"><span data-stu-id="54431-125">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[<span data-ttu-id="54431-126">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="54431-126">\<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="54431-127">Nie</span><span class="sxs-lookup"><span data-stu-id="54431-127">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[<span data-ttu-id="54431-128">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="54431-128">\<netMsmqBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="54431-129">Nie</span><span class="sxs-lookup"><span data-stu-id="54431-129">No</span></span>|  
  
     <span data-ttu-id="54431-130">Poniższy przykład kodu używa konfiguracji, aby określić powiązanie o nazwie `wsHttpBinding_Calculator` , który używa [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), zabezpieczenia wiadomości i bezpieczne sesje.</span><span class="sxs-lookup"><span data-stu-id="54431-130">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
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
  
     <span data-ttu-id="54431-131">Poniższy przykład kodu Określa, że [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), zabezpieczenia wiadomości i bezpieczne sesje służą do zabezpieczania `secureCalculator` usługi.</span><span class="sxs-lookup"><span data-stu-id="54431-131">The following code example specifies that the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="54431-132">Bezpieczne sesje mogą zostać wyłączone [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) , ustawiając `establishSecurityContext` atrybutu `false`.</span><span class="sxs-lookup"><span data-stu-id="54431-132">Secure sessions can be turned off for the [<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="54431-133">Dla innych powiązań dostarczanych przez system można tylko wyłączyć bezpiecznych sesji przez utworzenie niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="54431-133">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="54431-134">Aby określić, że usługa używa bezpiecznej sesji przy użyciu niestandardowego powiązania</span><span class="sxs-lookup"><span data-stu-id="54431-134">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
-   <span data-ttu-id="54431-135">Tworzenie niestandardowego powiązania, który określa, że komunikaty protokołu SOAP są chronione przez bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="54431-135">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="54431-136">Aby uzyskać więcej informacji na temat tworzenia niestandardowego powiązania, zobacz [jak: Dostosuj powiązania dostarczane przez System](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="54431-136">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="54431-137">Poniższy przykład kodu używa konfiguracji do określenia niestandardowego powiązania tej wiadomości, przy użyciu bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="54431-137">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
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
  
     <span data-ttu-id="54431-138">Poniższy przykład kodu tworzy niestandardowego powiązania, który używa <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> tryb uwierzytelniania uruchomienie bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="54431-138">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="54431-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54431-139">See also</span></span>
- [<span data-ttu-id="54431-140">Omówienie powiązań WCF</span><span class="sxs-lookup"><span data-stu-id="54431-140">WCF Bindings Overview</span></span>](../../../../docs/framework/wcf/bindings-overview.md)
