---
title: Programowanie zabezpieczeń WCF
description: Dowiedz się, jak utworzyć bezpieczną aplikację WCF, w tym uwierzytelnianie, poufność i integralność.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 8e77c667dd8904c10bbab88e1413690677cef53b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244988"
---
# <a name="programming-wcf-security"></a><span data-ttu-id="6ebf3-103">Programowanie zabezpieczeń WCF</span><span class="sxs-lookup"><span data-stu-id="6ebf3-103">Programming WCF Security</span></span>
<span data-ttu-id="6ebf3-104">W tym temacie opisano podstawowe zadania programistyczne służące do tworzenia aplikacji Secure Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6ebf3-104">This topic describes the fundamental programming tasks used to create a secure Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="6ebf3-105">W tym temacie omówiono jedynie uwierzytelnianie, poufność i integralność, nazywane zbiorczo *zabezpieczeniami transferu*.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-105">This topic covers only authentication, confidentiality, and integrity, collectively known as *transfer security*.</span></span> <span data-ttu-id="6ebf3-106">Ten temat nie obejmuje autoryzacji (kontrola dostępu do zasobów lub usług); Aby uzyskać informacje na temat autoryzacji, zobacz [autoryzacja](authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="6ebf3-106">This topic does not cover authorization (the control of access to resources or services); for information on authorization, see [Authorization](authorization-in-wcf.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ebf3-107">Aby dowiedzieć się więcej na temat pojęć związanych z zabezpieczeniami, szczególnie w odniesieniu do usługi WCF, zobacz zestaw samouczków i rozwiązań w witrynie MSDN w oparciu o [scenariusze, wzorce i wskazówki dotyczące implementacji dla ulepszeń usług sieci Web (WSE) 3,0](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="6ebf3-107">For a valuable introduction to security concepts, especially in regard to WCF, see the set of patterns and practices tutorials on MSDN at [Scenarios, Patterns, and Implementation Guidance for Web Services Enhancements (WSE) 3.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="6ebf3-108">Programowanie zabezpieczeń WCF opiera się na trzech krokach: tryb zabezpieczeń, typ poświadczeń klienta oraz wartości poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-108">Programming WCF security is based on three steps setting the following: the security mode, a client credential type, and the credential values.</span></span> <span data-ttu-id="6ebf3-109">Kroki te można wykonać za pomocą kodu lub konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-109">You can perform these steps either through code or configuration.</span></span>  
  
## <a name="setting-the-security-mode"></a><span data-ttu-id="6ebf3-110">Ustawianie trybu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="6ebf3-110">Setting the Security Mode</span></span>  
 <span data-ttu-id="6ebf3-111">Poniżej objaśniono ogólne kroki programowania z trybem zabezpieczeń w programie WCF:</span><span class="sxs-lookup"><span data-stu-id="6ebf3-111">The following explains the general steps for programming with the security mode in WCF:</span></span>  
  
1. <span data-ttu-id="6ebf3-112">Wybierz jedno ze wstępnie zdefiniowanych powiązań odpowiednie dla wymagań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-112">Select one of the predefined bindings appropriate to your application requirements.</span></span> <span data-ttu-id="6ebf3-113">Aby uzyskać listę opcji powiązań, zobacz [powiązania dostarczone przez system](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="6ebf3-113">For a list of the binding choices, see [System-Provided Bindings](../system-provided-bindings.md).</span></span> <span data-ttu-id="6ebf3-114">Domyślnie niemal każde powiązanie ma włączone zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-114">By default, nearly every binding has security enabled.</span></span> <span data-ttu-id="6ebf3-115">Jedynym wyjątkiem jest <xref:System.ServiceModel.BasicHttpBinding> Klasa (przy użyciu konfiguracji, a [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) ).</span><span class="sxs-lookup"><span data-stu-id="6ebf3-115">The one exception is the <xref:System.ServiceModel.BasicHttpBinding> class (using configuration, the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)).</span></span>  
  
     <span data-ttu-id="6ebf3-116">Wybrane powiązanie określa transport.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-116">The binding you select determines the transport.</span></span> <span data-ttu-id="6ebf3-117">Na przykład <xref:System.ServiceModel.WSHttpBinding> używa protokołu HTTP jako transportu; <xref:System.ServiceModel.NetTcpBinding> używa protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-117">For example, <xref:System.ServiceModel.WSHttpBinding> uses HTTP as the transport; <xref:System.ServiceModel.NetTcpBinding> uses TCP.</span></span>  
  
2. <span data-ttu-id="6ebf3-118">Wybierz jeden z trybów zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-118">Select one of the security modes for the binding.</span></span> <span data-ttu-id="6ebf3-119">Należy zauważyć, że wybrane powiązanie określa dostępne opcje trybu.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-119">Note that the binding you select determines the available mode choices.</span></span> <span data-ttu-id="6ebf3-120">Na przykład nie <xref:System.ServiceModel.WSDualHttpBinding> zezwala na zabezpieczenia transportu (nie jest to opcja).</span><span class="sxs-lookup"><span data-stu-id="6ebf3-120">For example, the <xref:System.ServiceModel.WSDualHttpBinding> does not allow transport security (it is not an option).</span></span> <span data-ttu-id="6ebf3-121">Analogicznie, ani <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> <xref:System.ServiceModel.NetNamedPipeBinding> zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-121">Similarly, neither the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nor the <xref:System.ServiceModel.NetNamedPipeBinding> allows message security.</span></span>  
  
     <span data-ttu-id="6ebf3-122">Masz trzy opcje:</span><span class="sxs-lookup"><span data-stu-id="6ebf3-122">You have three choices:</span></span>  
  
    1. `Transport`  
  
         <span data-ttu-id="6ebf3-123">Zabezpieczenia transportu są zależne od mechanizmu wybranego przez Ciebie powiązania.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-123">Transport security depends on the mechanism that the binding you have selected uses.</span></span> <span data-ttu-id="6ebf3-124">Na przykład, jeśli używasz, `WSHttpBinding` mechanizm zabezpieczeń jest SSL (SSL) (również mechanizm protokołu HTTPS).</span><span class="sxs-lookup"><span data-stu-id="6ebf3-124">For example, if you are using `WSHttpBinding` then the security mechanism is Secure Sockets Layer (SSL) (also the mechanism for the HTTPS protocol).</span></span> <span data-ttu-id="6ebf3-125">Ogólnie mówiąc, główną zaletą zabezpieczeń transportu jest to, że zapewnia ona dobrą przepływność niezależnie od używanego transportu.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-125">Generally speaking, the main advantage of transport security is that it delivers good throughput no matter which transport you are using.</span></span> <span data-ttu-id="6ebf3-126">Jednak ma dwa ograniczenia: Pierwszy polega na tym, że mechanizm transportu wymusza typ poświadczeń używany do uwierzytelniania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-126">However, it does have two limitations: The first is that the transport mechanism dictates the credential type used to authenticate a user.</span></span> <span data-ttu-id="6ebf3-127">Jest to wadą tylko wtedy, gdy usługa musi współpracować z innymi usługami, które wymagają różnych typów poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-127">This is a drawback only if a service needs to interoperate with other services that demand different types of credentials.</span></span> <span data-ttu-id="6ebf3-128">Drugim jest to, że ze względu na to, że zabezpieczenia nie są stosowane na poziomie komunikatu, zabezpieczenia są implementowane w sposób przeskokowy, a nie na kompletny.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-128">The second is that, because the security is not applied at the message level, security is implemented in a hop-by-hop manner rather than end-to-end.</span></span> <span data-ttu-id="6ebf3-129">Ten ostatni problem występuje tylko wtedy, gdy ścieżka komunikatu między klientem a usługą obejmuje pośredników.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-129">This latter limitation is an issue only if the message path between client and service includes intermediaries.</span></span> <span data-ttu-id="6ebf3-130">Aby uzyskać więcej informacji o tym, który transport ma być używany, zobacz [Wybieranie transportu](choosing-a-transport.md).</span><span class="sxs-lookup"><span data-stu-id="6ebf3-130">For more information about which transport to use, see [Choosing a Transport](choosing-a-transport.md).</span></span> <span data-ttu-id="6ebf3-131">Aby uzyskać więcej informacji o korzystaniu z zabezpieczeń transportu, zobacz [Omówienie zabezpieczeń transportu](transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6ebf3-131">For more information about using transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>  
  
    2. `Message`  
  
         <span data-ttu-id="6ebf3-132">Zabezpieczenia komunikatów oznacza, że każdy komunikat zawiera niezbędne nagłówki i dane, aby zachować komunikat bezpieczny.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-132">Message security means that every message includes the necessary headers and data to keep the message secure.</span></span> <span data-ttu-id="6ebf3-133">Ponieważ kompozycja nagłówków jest różna, można dołączyć dowolną liczbę poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-133">Because the composition of the headers varies, you can include any number of credentials.</span></span> <span data-ttu-id="6ebf3-134">Jest to czynnik, jeśli pracujesz z innymi usługami, które wymagają określonego typu poświadczeń, których mechanizm transportu nie może dostarczyć, lub jeśli komunikat musi być używany z więcej niż jedną usługą, gdzie każda usługa wymaga innego typu poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-134">This becomes a factor if you are interoperating with other services that demand a specific credential type that a transport mechanism can't supply, or if the message must be used with more than one service, where each service demands a different credential type.</span></span>  
  
         <span data-ttu-id="6ebf3-135">Aby uzyskać więcej informacji, zobacz [zabezpieczenia komunikatów](message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="6ebf3-135">For more information, see [Message Security](message-security-in-wcf.md).</span></span>  
  
    3. `TransportWithMessageCredential`  
  
         <span data-ttu-id="6ebf3-136">Ten wybór używa warstwy transportu do zabezpieczenia transferu wiadomości, podczas gdy każdy komunikat zawiera zaawansowane poświadczenia, które są wymagane przez inne usługi.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-136">This choice uses the transport layer to secure the message transfer, while every message includes the rich credentials other services need.</span></span> <span data-ttu-id="6ebf3-137">Obejmuje to zalety wydajności transportu z wykorzystaniem bogatych poświadczeń w zakresie zabezpieczeń komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-137">This combines the performance advantage of transport security with the rich credentials advantage of message security.</span></span> <span data-ttu-id="6ebf3-138">Jest on dostępny z następującymi powiązaniami: <xref:System.ServiceModel.BasicHttpBinding> , <xref:System.ServiceModel.WSFederationHttpBinding> , <xref:System.ServiceModel.NetPeerTcpBinding> i <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="6ebf3-138">This is available with the following bindings: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, and <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3. <span data-ttu-id="6ebf3-139">Jeśli zdecydujesz się korzystać z zabezpieczeń transportu dla protokołu HTTP (innymi słowy, HTTPS), należy również skonfigurować hosta z certyfikatem SSL i włączyć protokół SSL na porcie.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-139">If you decide to use transport security for HTTP (in other words, HTTPS), you must also configure the host with an SSL certificate and enable SSL on a port.</span></span> <span data-ttu-id="6ebf3-140">Aby uzyskać więcej informacji, zobacz [zabezpieczenia transportu HTTP](http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="6ebf3-140">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
4. <span data-ttu-id="6ebf3-141">Jeśli używasz usługi <xref:System.ServiceModel.WSHttpBinding> i nie musisz ustanawiać bezpiecznej sesji, ustaw <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> Właściwość na wartość `false` .</span><span class="sxs-lookup"><span data-stu-id="6ebf3-141">If you are using the <xref:System.ServiceModel.WSHttpBinding> and do not need to establish a secure session, set the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="6ebf3-142">Bezpieczna sesja odbywa się, gdy klient i usługa tworzą kanał przy użyciu klucza symetrycznego (zarówno klient, jak i serwer używają tego samego klucza dla długości konwersacji, dopóki okno dialogowe nie zostanie zamknięte).</span><span class="sxs-lookup"><span data-stu-id="6ebf3-142">A secure session occurs when a client and service create a channel using a symmetric key (both client and server use the same key for the length of a conversation, until the dialog is closed).</span></span>  
  
## <a name="setting-the-client-credential-type"></a><span data-ttu-id="6ebf3-143">Ustawianie typu poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="6ebf3-143">Setting the Client Credential Type</span></span>  
 <span data-ttu-id="6ebf3-144">W razie potrzeby wybierz odpowiedni typ poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-144">Select a client credential type as appropriate.</span></span> <span data-ttu-id="6ebf3-145">Aby uzyskać więcej informacji, zobacz [Wybieranie typu poświadczeń](selecting-a-credential-type.md).</span><span class="sxs-lookup"><span data-stu-id="6ebf3-145">For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).</span></span> <span data-ttu-id="6ebf3-146">Dostępne są następujące typy poświadczeń klienta:</span><span class="sxs-lookup"><span data-stu-id="6ebf3-146">The following client credential types are available:</span></span>  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 <span data-ttu-id="6ebf3-147">W zależności od sposobu ustawienia trybu należy ustawić typ poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-147">Depending on how you set the mode, you must set the credential type.</span></span> <span data-ttu-id="6ebf3-148">Na przykład jeśli wybrano `wsHttpBinding` i ustawisz tryb na "Message", można również ustawić `clientCredentialType` atrybut elementu Message na jedną z następujących wartości: `None` , `Windows` ,, `UserName` `Certificate` , i `IssuedToken` , jak pokazano w poniższym przykładzie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-148">For example, if you have selected the `wsHttpBinding`, and have set the mode to "Message," then you can also set the `clientCredentialType` attribute of the Message element to one of the following values: `None`, `Windows`, `UserName`, `Certificate`, and `IssuedToken`, as shown in the following configuration example.</span></span>  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>
  </wsHttpBinding>
</bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="6ebf3-149">Lub w kodzie:</span><span class="sxs-lookup"><span data-stu-id="6ebf3-149">Or in code:</span></span>  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a><span data-ttu-id="6ebf3-150">Ustawianie wartości poświadczeń usługi</span><span class="sxs-lookup"><span data-stu-id="6ebf3-150">Setting Service Credential Values</span></span>  
 <span data-ttu-id="6ebf3-151">Po wybraniu typu poświadczeń klienta należy ustawić rzeczywiste poświadczenia usługi i klienta, które mają być używane.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-151">Once you select a client credential type, you must set the actual credentials for the service and client to use.</span></span> <span data-ttu-id="6ebf3-152">W usłudze poświadczenia są ustawiane za pomocą <xref:System.ServiceModel.Description.ServiceCredentials> klasy i zwracane przez <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> Właściwość <xref:System.ServiceModel.ServiceHostBase> klasy.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-152">On the service, credentials are set using the <xref:System.ServiceModel.Description.ServiceCredentials> class and returned by the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property of the <xref:System.ServiceModel.ServiceHostBase> class.</span></span> <span data-ttu-id="6ebf3-153">Powiązanie w użyciu sugeruje typ poświadczeń usługi, wybrany tryb zabezpieczeń i typ poświadczenia klienta.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-153">The binding in use implies the service credential type, the security mode chosen, and the type of the client credential.</span></span> <span data-ttu-id="6ebf3-154">Poniższy kod ustawia certyfikat dla poświadczenia usługi.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-154">The following code sets a certificate for a service credential.</span></span>  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a><span data-ttu-id="6ebf3-155">Ustawianie wartości poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="6ebf3-155">Setting Client Credential Values</span></span>  
 <span data-ttu-id="6ebf3-156">Na kliencie Ustaw wartości poświadczeń klienta przy użyciu <xref:System.ServiceModel.Description.ClientCredentials> klasy i zwrócone przez <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Właściwość <xref:System.ServiceModel.ClientBase%601> klasy.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-156">On the client, set client credential values using the <xref:System.ServiceModel.Description.ClientCredentials> class and returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="6ebf3-157">Poniższy kod służy do ustawiania certyfikatu jako poświadczenia na kliencie przy użyciu protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="6ebf3-157">The following code sets a certificate as a credential on a client using the TCP protocol.</span></span>  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6ebf3-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ebf3-158">See also</span></span>

- [<span data-ttu-id="6ebf3-159">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="6ebf3-159">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- [<span data-ttu-id="6ebf3-160">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="6ebf3-160">Common Security Scenarios</span></span>](common-security-scenarios.md)
