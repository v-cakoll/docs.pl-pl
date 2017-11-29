---
title: "Programowanie zabezpieczeń WCF"
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
helpviewer_keywords: message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
caps.latest.revision: "25"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 5f61eb200c141f95b24fec1a424ce7b92d8559cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="programming-wcf-security"></a><span data-ttu-id="da1c1-102">Programowanie zabezpieczeń WCF</span><span class="sxs-lookup"><span data-stu-id="da1c1-102">Programming WCF Security</span></span>
<span data-ttu-id="da1c1-103">W tym temacie opisano podstawowe zadania programowania, używany do tworzenia bezpiecznego [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da1c1-103">This topic describes the fundamental programming tasks used to create a secure [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="da1c1-104">W tym temacie omówiono tylko uwierzytelnianie, poufność i integralność, nazywanych zbiorczo *transferu zabezpieczeń*.</span><span class="sxs-lookup"><span data-stu-id="da1c1-104">This topic covers only authentication, confidentiality, and integrity, collectively known as *transfer security*.</span></span> <span data-ttu-id="da1c1-105">W tym temacie nie opisano autoryzacji (kontrola dostępu do zasobów lub usług); informacje dotyczące autoryzacji znajdują się w temacie [autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="da1c1-105">This topic does not cover authorization (the control of access to resources or services); for information on authorization, see [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da1c1-106">Wprowadzenie przydatna do pojęć związanych z zabezpieczeniami, zwłaszcza w odniesieniu do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], zobacz zestaw samouczki wzorców i rozwiązań w witrynie MSDN w [scenariuszy, wzorców i wskazówki dotyczące implementacji dla sieci Web ulepszenia usług (WSE) 3.0](http://go.microsoft.com/fwlink/?LinkID=88250).</span><span class="sxs-lookup"><span data-stu-id="da1c1-106">For a valuable introduction to security concepts, especially in regard to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see the set of patterns and practices tutorials on MSDN at [Scenarios, Patterns, and Implementation Guidance for Web Services Enhancements (WSE) 3.0](http://go.microsoft.com/fwlink/?LinkID=88250).</span></span>  
  
 <span data-ttu-id="da1c1-107">Programowanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń opiera się na trzy kroki następujące ustawienia: tryb zabezpieczeń, typu poświadczeń klienta i wartości poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="da1c1-107">Programming [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security is based on three steps setting the following: the security mode, a client credential type, and the credential values.</span></span> <span data-ttu-id="da1c1-108">Można wykonywać następujące czynności, za pomocą kodu lub konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="da1c1-108">You can perform these steps either through code or configuration.</span></span>  
  
## <a name="setting-the-security-mode"></a><span data-ttu-id="da1c1-109">Ustawianie trybu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="da1c1-109">Setting the Security Mode</span></span>  
 <span data-ttu-id="da1c1-110">Następujące przedstawiono ogólne kroki do programowania za pomocą trybu zabezpieczeń w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="da1c1-110">The following explains the general steps for programming with the security mode in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
1.  <span data-ttu-id="da1c1-111">Wybierz jeden z wstępnie zdefiniowanych powiązań odpowiednią do wymagań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da1c1-111">Select one of the predefined bindings appropriate to your application requirements.</span></span> <span data-ttu-id="da1c1-112">Listę dostępnych opcji Powiązanie zawiera [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="da1c1-112">For a list of the binding choices, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="da1c1-113">Domyślnie niemal każde powiązanie ma włączoną obsługą zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="da1c1-113">By default, nearly every binding has security enabled.</span></span> <span data-ttu-id="da1c1-114">Jedynym wyjątkiem jest <xref:System.ServiceModel.BasicHttpBinding> klasy (za pomocą konfiguracji, [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).</span><span class="sxs-lookup"><span data-stu-id="da1c1-114">The one exception is the <xref:System.ServiceModel.BasicHttpBinding> class (using configuration, the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).</span></span>  
  
     <span data-ttu-id="da1c1-115">Wybrane powiązanie określa transportu.</span><span class="sxs-lookup"><span data-stu-id="da1c1-115">The binding you select determines the transport.</span></span> <span data-ttu-id="da1c1-116">Na przykład <xref:System.ServiceModel.WSHttpBinding> korzysta z protokołu HTTP jako transportu; <xref:System.ServiceModel.NetTcpBinding> protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="da1c1-116">For example, <xref:System.ServiceModel.WSHttpBinding> uses HTTP as the transport; <xref:System.ServiceModel.NetTcpBinding> uses TCP.</span></span>  
  
2.  <span data-ttu-id="da1c1-117">Wybierz jeden z trybów zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="da1c1-117">Select one of the security modes for the binding.</span></span> <span data-ttu-id="da1c1-118">Należy pamiętać, że wybrane powiązanie Określa tryb dostępnych opcji.</span><span class="sxs-lookup"><span data-stu-id="da1c1-118">Note that the binding you select determines the available mode choices.</span></span> <span data-ttu-id="da1c1-119">Na przykład <xref:System.ServiceModel.WSDualHttpBinding> nie zezwala na zabezpieczeń transportu (nie jest ona opcję).</span><span class="sxs-lookup"><span data-stu-id="da1c1-119">For example, the <xref:System.ServiceModel.WSDualHttpBinding> does not allow transport security (it is not an option).</span></span> <span data-ttu-id="da1c1-120">Podobnie, ani <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ani <xref:System.ServiceModel.NetNamedPipeBinding> umożliwia zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="da1c1-120">Similarly, neither the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nor the <xref:System.ServiceModel.NetNamedPipeBinding> allows message security.</span></span>  
  
     <span data-ttu-id="da1c1-121">Wyświetlane są trzy opcje:</span><span class="sxs-lookup"><span data-stu-id="da1c1-121">You have three choices:</span></span>  
  
    1.  `Transport`  
  
         <span data-ttu-id="da1c1-122">Zabezpieczenia transportu zależy od mechanizm, który używa wybranego powiązania.</span><span class="sxs-lookup"><span data-stu-id="da1c1-122">Transport security depends on the mechanism that the binding you have selected uses.</span></span> <span data-ttu-id="da1c1-123">Na przykład, jeśli używasz `WSHttpBinding` mechanizm zabezpieczeń jest Secure Sockets Layer (SSL) (również mechanizm dla protokołu HTTPS).</span><span class="sxs-lookup"><span data-stu-id="da1c1-123">For example, if you are using `WSHttpBinding` then the security mechanism is Secure Sockets Layer (SSL) (also the mechanism for the HTTPS protocol).</span></span> <span data-ttu-id="da1c1-124">Główną zaletą zabezpieczeń transportu jest ogólnie rzecz biorąc, zapewnia dobre przepływności, niezależnie od tego, które transportu są używane.</span><span class="sxs-lookup"><span data-stu-id="da1c1-124">Generally speaking, the main advantage of transport security is that it delivers good throughput no matter which transport you are using.</span></span> <span data-ttu-id="da1c1-125">Jednak mieć dwa ograniczenia: pierwsza to, że mechanizm transportu nakazują typ poświadczenia używane do uwierzytelnienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="da1c1-125">However, it does have two limitations: The first is that the transport mechanism dictates the credential type used to authenticate a user.</span></span> <span data-ttu-id="da1c1-126">Wadą jest tylko wtedy, gdy usługa musi współdziałać z innymi usługami, które wymagają różnych rodzajów poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="da1c1-126">This is a drawback only if a service needs to interoperate with other services that demand different types of credentials.</span></span> <span data-ttu-id="da1c1-127">Drugim jest, ponieważ nie zastosowano zabezpieczenia na poziomie komunikatu, zabezpieczeń jest zaimplementowana w sposób przeskoku przeskoku zamiast end-to-end.</span><span class="sxs-lookup"><span data-stu-id="da1c1-127">The second is that, because the security is not applied at the message level, security is implemented in a hop-by-hop manner rather than end-to-end.</span></span> <span data-ttu-id="da1c1-128">To ograniczenie ostatnie jest problem tylko, jeśli ścieżka wiadomości między klientem a usługą zawiera pośredników.</span><span class="sxs-lookup"><span data-stu-id="da1c1-128">This latter limitation is an issue only if the message path between client and service includes intermediaries.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="da1c1-129">które transportu do użycia, zobacz [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).</span><span class="sxs-lookup"><span data-stu-id="da1c1-129"> which transport to use, see [Choosing a Transport](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="da1c1-130">za pomocą zabezpieczeń transportu, zobacz [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="da1c1-130"> using transport security, see [Transport Security Overview](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span></span>  
  
    2.  `Message`  
  
         <span data-ttu-id="da1c1-131">Zabezpieczenia komunikatów oznacza, że każdy komunikat zawiera niezbędne nagłówki i bezpieczeństwo danych, aby zachować wiadomości.</span><span class="sxs-lookup"><span data-stu-id="da1c1-131">Message security means that every message includes the necessary headers and data to keep the message secure.</span></span> <span data-ttu-id="da1c1-132">Ponieważ kompozycji nagłówki różni się może zawierać dowolną liczbę poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="da1c1-132">Because the composition of the headers varies, you can include any number of credentials.</span></span> <span data-ttu-id="da1c1-133">To staje się czynnikiem, czy możesz są współdziałanie z innymi usługami tego żądanie typu poświadczenie mechanizm transportu nie może dostarczyć, czy wiadomości musi być używany z więcej niż jedna usługa, gdzie każda usługa wymaga typu różnych poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="da1c1-133">This becomes a factor if you are interoperating with other services that demand a specific credential type that a transport mechanism can't supply, or if the message must be used with more than one service, where each service demands a different credential type.</span></span>  
  
         [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="da1c1-134">[Zabezpieczenia wiadomości](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="da1c1-134"> [Message Security](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
    3.  `TransportWithMessageCredential`  
  
         <span data-ttu-id="da1c1-135">Ten wybór używa Warstwa transportu do bezpiecznego transferu komunikatów, podczas każdej wiadomości zawiera bogaty poświadczenia muszą innych usług.</span><span class="sxs-lookup"><span data-stu-id="da1c1-135">This choice uses the transport layer to secure the message transfer, while every message includes the rich credentials other services need.</span></span> <span data-ttu-id="da1c1-136">Łączy wydajności zaletą zabezpieczeń transportu i zalety zaawansowanych poświadczenia zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="da1c1-136">This combines the performance advantage of transport security with the rich credentials advantage of message security.</span></span> <span data-ttu-id="da1c1-137">To ustawienie jest dostępne z powiązaniami następujących: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, i <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="da1c1-137">This is available with the following bindings: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, and <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3.  <span data-ttu-id="da1c1-138">Jeśli zdecydujesz się użyć zabezpieczeń transportu dla protokołu HTTP (innymi słowy, HTTPS), należy również skonfigurować hosta za pomocą certyfikatu SSL i Włącz protokół SSL na porcie.</span><span class="sxs-lookup"><span data-stu-id="da1c1-138">If you decide to use transport security for HTTP (in other words, HTTPS), you must also configure the host with an SSL certificate and enable SSL on a port.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="da1c1-139">[Zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="da1c1-139"> [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
4.  <span data-ttu-id="da1c1-140">Jeśli używasz <xref:System.ServiceModel.WSHttpBinding> i nie ma potrzeby nawiązywania bezpiecznej sesji, należy ustawić <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwości `false`.</span><span class="sxs-lookup"><span data-stu-id="da1c1-140">If you are using the <xref:System.ServiceModel.WSHttpBinding> and do not need to establish a secure session, set the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="da1c1-141">Bezpieczna sesja występuje, gdy klient i usługa utworzyć kanał za pomocą klucza symetrycznego (klient i serwer używać tego samego klucza długości konwersację, do czasu zamknięcia okna dialogowego).</span><span class="sxs-lookup"><span data-stu-id="da1c1-141">A secure session occurs when a client and service create a channel using a symmetric key (both client and server use the same key for the length of a conversation, until the dialog is closed).</span></span>  
  
## <a name="setting-the-client-credential-type"></a><span data-ttu-id="da1c1-142">Ustawienie typu poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="da1c1-142">Setting the Client Credential Type</span></span>  
 <span data-ttu-id="da1c1-143">Wybierz typ poświadczeń klienta zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="da1c1-143">Select a client credential type as appropriate.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="da1c1-144">[Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).</span><span class="sxs-lookup"><span data-stu-id="da1c1-144"> [Selecting a Credential Type](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).</span></span> <span data-ttu-id="da1c1-145">Dostępne są następujące typy poświadczeń klienta:</span><span class="sxs-lookup"><span data-stu-id="da1c1-145">The following client credential types are available:</span></span>  
  
-   `Windows`  
  
-   `Certificate`  
  
-   `Digest`  
  
-   `Basic`  
  
-   `UserName`  
  
-   `NTLM`  
  
-   `IssuedToken`  
  
 <span data-ttu-id="da1c1-146">W zależności od tego, jak możesz ustawić tryb należy ustawić typ poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="da1c1-146">Depending on how you set the mode, you must set the credential type.</span></span> <span data-ttu-id="da1c1-147">Na przykład, jeśli wybrano `wsHttpBinding`, ustawiono tryb "Komunikat", a następnie można również ustawić `clientCredentialType` atrybut elementu wiadomości do jednej z następujących wartości: `None`, `Windows`, `UserName`, `Certificate` , a `IssuedToken`, jak pokazano w poniższym przykładzie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="da1c1-147">For example, if you have selected the `wsHttpBinding`, and have set the mode to "Message," then you can also set the `clientCredentialType` attribute of the Message element to one of the following values: `None`, `Windows`, `UserName`, `Certificate`, and `IssuedToken`, as shown in the following configuration example.</span></span>  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>  
</bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="da1c1-148">Lub w kodzie:</span><span class="sxs-lookup"><span data-stu-id="da1c1-148">Or in code:</span></span>  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a><span data-ttu-id="da1c1-149">Ustawienie usługi poświadczeń wartości</span><span class="sxs-lookup"><span data-stu-id="da1c1-149">Setting Service Credential Values</span></span>  
 <span data-ttu-id="da1c1-150">Po wybraniu typu poświadczeń klienta, należy ustawić rzeczywiste poświadczenia dla usługi i klienta do używania.</span><span class="sxs-lookup"><span data-stu-id="da1c1-150">Once you select a client credential type, you must set the actual credentials for the service and client to use.</span></span> <span data-ttu-id="da1c1-151">W usłudze, poświadczenia są ustawiane przy użyciu <xref:System.ServiceModel.Description.ServiceCredentials> klasy i zwrócony przez <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwość <xref:System.ServiceModel.ServiceHostBase> klasy.</span><span class="sxs-lookup"><span data-stu-id="da1c1-151">On the service, credentials are set using the <xref:System.ServiceModel.Description.ServiceCredentials> class and returned by the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property of the <xref:System.ServiceModel.ServiceHostBase> class.</span></span> <span data-ttu-id="da1c1-152">Używane powiązanie oznacza typ poświadczeń usługi, wybrany tryb zabezpieczeń i typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="da1c1-152">The binding in use implies the service credential type, the security mode chosen, and the type of the client credential.</span></span> <span data-ttu-id="da1c1-153">Poniższy kod ustawia certyfikatu dla poświadczenia usługi.</span><span class="sxs-lookup"><span data-stu-id="da1c1-153">The following code sets a certificate for a service credential.</span></span>  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a><span data-ttu-id="da1c1-154">Ustawienie wartości poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="da1c1-154">Setting Client Credential Values</span></span>  
 <span data-ttu-id="da1c1-155">Na komputerze klienckim, należy ustawić wartości poświadczeń klienta przy użyciu <xref:System.ServiceModel.Description.ClientCredentials> klasy i zwrócony przez <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość <xref:System.ServiceModel.ClientBase%601> klasy.</span><span class="sxs-lookup"><span data-stu-id="da1c1-155">On the client, set client credential values using the <xref:System.ServiceModel.Description.ClientCredentials> class and returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="da1c1-156">Poniższy kod ustawia certyfikatu jako poświadczeń klienta przy użyciu protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="da1c1-156">The following code sets a certificate as a credential on a client using the TCP protocol.</span></span>  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="da1c1-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da1c1-157">See Also</span></span>  
 [<span data-ttu-id="da1c1-158">Programowanie podstawowe usługi WCF</span><span class="sxs-lookup"><span data-stu-id="da1c1-158">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="da1c1-159">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="da1c1-159">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
