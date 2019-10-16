---
title: 'Instrukcje: Ustawianie trybu zabezpieczeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: 9b9e25cbafb6387b4584a21fd642d80bc41cd8dc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320893"
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="59e8e-102">Instrukcje: Ustawianie trybu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="59e8e-102">How to: Set the Security Mode</span></span>

<span data-ttu-id="59e8e-103">Zabezpieczenia Windows Communication Foundation (WCF) mają trzy popularne tryby zabezpieczeń, które znajdują się w większości wstępnie zdefiniowanych powiązań: transport, Message i "transport z poświadczeniami wiadomości".</span><span class="sxs-lookup"><span data-stu-id="59e8e-103">Windows Communication Foundation (WCF) security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="59e8e-104">Dwa dodatkowe tryby są specyficzne dla dwóch powiązań: tryb "transport-Credential Only" znaleziony w <xref:System.ServiceModel.BasicHttpBinding> i tryb "oba", który znajduje się w <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="59e8e-104">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="59e8e-105">Jednak ten temat koncentruje się na trzech wspólnych trybach zabezpieczeń: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message> i <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="59e8e-105">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>

<span data-ttu-id="59e8e-106">Należy zauważyć, że nie każde wstępnie zdefiniowane powiązanie obsługuje wszystkie te tryby.</span><span class="sxs-lookup"><span data-stu-id="59e8e-106">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="59e8e-107">Ten temat ustawia tryb z klasami <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.NetTcpBinding> i pokazuje, jak ustawić tryb programowo i za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="59e8e-107">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>

<span data-ttu-id="59e8e-108">Aby uzyskać więcej informacji, zobacz zabezpieczenia WCF, zobacz [Omówienie zabezpieczeń](./feature-details/security-overview.md), [Zabezpieczanie usług](securing-services.md)i [Zabezpieczanie usług i klientów](./feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="59e8e-108">For more information, see WCF security, see [Security Overview](./feature-details/security-overview.md), [Securing Services](securing-services.md), and [Securing Services and Clients](./feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="59e8e-109">Aby uzyskać więcej informacji na temat trybu transportu i komunikatu, zobacz [zabezpieczenia transportu](./feature-details/transport-security.md) i [zabezpieczenia komunikatów](./feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="59e8e-109">For more information about transport mode and message, see [Transport Security](./feature-details/transport-security.md) and [Message Security](./feature-details/message-security-in-wcf.md).</span></span>

## <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="59e8e-110">Aby ustawić tryb zabezpieczeń w kodzie</span><span class="sxs-lookup"><span data-stu-id="59e8e-110">To set the security mode in code</span></span>

1. <span data-ttu-id="59e8e-111">Utwórz wystąpienie klasy powiązania, której używasz.</span><span class="sxs-lookup"><span data-stu-id="59e8e-111">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="59e8e-112">Aby uzyskać listę wstępnie zdefiniowanych powiązań, zobacz [powiązania dostarczone przez system](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="59e8e-112">For a list of predefined bindings, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="59e8e-113">Ten przykład tworzy wystąpienie klasy <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="59e8e-113">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

2. <span data-ttu-id="59e8e-114">Ustaw właściwość `Mode` obiektu zwróconego przez właściwość `Security`.</span><span class="sxs-lookup"><span data-stu-id="59e8e-114">Set the `Mode` property of the object returned by the `Security` property.</span></span>

     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]

     <span data-ttu-id="59e8e-115">Alternatywnie można ustawić tryb na komunikat, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="59e8e-115">Alternatively, set the mode to message, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]

     <span data-ttu-id="59e8e-116">Lub ustaw tryb transportu z poświadczeniami wiadomości, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="59e8e-116">Or set the mode to transport with message credentials, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]

3. <span data-ttu-id="59e8e-117">Można również ustawić tryb w konstruktorze powiązania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="59e8e-117">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]

## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="59e8e-118">Ustawianie właściwości ClientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="59e8e-118">Setting the ClientCredentialType Property</span></span>

<span data-ttu-id="59e8e-119">Ustawienie trybu na jedną z trzech wartości określa sposób ustawiania właściwości `ClientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="59e8e-119">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="59e8e-120">Na przykład przy użyciu klasy <xref:System.ServiceModel.WSHttpBinding> ustawienie Tryb na `Transport` oznacza, że właściwość <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> klasy <xref:System.ServiceModel.HttpTransportSecurity> ma mieć odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="59e8e-120">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="59e8e-121">Aby ustawić właściwość ClientCredentialtype dla trybu transportu</span><span class="sxs-lookup"><span data-stu-id="59e8e-121">To set the ClientCredentialType property for Transport mode</span></span>

1. <span data-ttu-id="59e8e-122">Utwórz wystąpienie powiązania.</span><span class="sxs-lookup"><span data-stu-id="59e8e-122">Create an instance of the binding.</span></span>

2. <span data-ttu-id="59e8e-123">Ustaw właściwość `Mode` na `Transport`.</span><span class="sxs-lookup"><span data-stu-id="59e8e-123">Set the `Mode` property to `Transport`.</span></span>

3. <span data-ttu-id="59e8e-124">Ustaw właściwość `ClientCredential` na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="59e8e-124">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="59e8e-125">Poniższy kod ustawia właściwość na `Windows`.</span><span class="sxs-lookup"><span data-stu-id="59e8e-125">The following code sets the property to `Windows`.</span></span>

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="59e8e-126">Aby ustawić właściwość ClientCredentialtype dla trybu komunikatu</span><span class="sxs-lookup"><span data-stu-id="59e8e-126">To set the ClientCredentialType property for Message mode</span></span>

1. <span data-ttu-id="59e8e-127">Utwórz wystąpienie powiązania.</span><span class="sxs-lookup"><span data-stu-id="59e8e-127">Create an instance of the binding.</span></span>

2. <span data-ttu-id="59e8e-128">Ustaw właściwość `Mode` na `Message`.</span><span class="sxs-lookup"><span data-stu-id="59e8e-128">Set the `Mode` property to `Message`.</span></span>

3. <span data-ttu-id="59e8e-129">Ustaw właściwość `ClientCredential` na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="59e8e-129">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="59e8e-130">Poniższy kod ustawia właściwość na `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="59e8e-130">The following code sets the property to `Certificate`.</span></span>

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="59e8e-131">Aby ustawić tryb i Właściwość ClientCredentialtype w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="59e8e-131">To set the Mode and ClientCredentialType property in configuration</span></span>

1. <span data-ttu-id="59e8e-132">Dodaj odpowiedni element powiązania do elementu [\<bindings >](../configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="59e8e-132">Add an appropriate binding element to the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="59e8e-133">Poniższy przykład dodaje element [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="59e8e-133">The following example adds a [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

2. <span data-ttu-id="59e8e-134">Dodaj element `<binding>` i ustaw jego atrybut `name` na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="59e8e-134">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="59e8e-135">Dodaj element `<security>` i ustaw atrybut `mode` na `Message`, `Transport` lub `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="59e8e-135">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

4. <span data-ttu-id="59e8e-136">Jeśli tryb jest ustawiony na `Transport`, Dodaj element `<transport>` i ustaw odpowiednią wartość atrybutu `clientCredential`.</span><span class="sxs-lookup"><span data-stu-id="59e8e-136">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>

     <span data-ttu-id="59e8e-137">Poniższy przykład ustawia tryb na "`Transport"`, a następnie ustawia atrybut `clientCredentialType` elementu `<transport>` na" `Windows"`.</span><span class="sxs-lookup"><span data-stu-id="59e8e-137">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="59e8e-138">Alternatywnie można ustawić wartość `security mode` na "`Message"`", po którym następuje element `<"message">`.</span><span class="sxs-lookup"><span data-stu-id="59e8e-138">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="59e8e-139">Ten przykład ustawia wartość `clientCredentialType` na "`Certificate"`.</span><span class="sxs-lookup"><span data-stu-id="59e8e-139">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="59e8e-140">Użycie wartości <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> jest szczególnym przypadkiem i wyjaśniono poniżej.</span><span class="sxs-lookup"><span data-stu-id="59e8e-140">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>

### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="59e8e-141">Korzystanie z TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="59e8e-141">Using TransportWithMessageCredential</span></span>

<span data-ttu-id="59e8e-142">Podczas ustawiania trybu zabezpieczeń na `TransportWithMessageCredential`, transport określa rzeczywisty mechanizm, który zapewnia zabezpieczenia na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="59e8e-142">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="59e8e-143">Na przykład protokół HTTP używa protokołu SSL (SSL) za pośrednictwem protokołu HTTP (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="59e8e-143">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="59e8e-144">W związku z tym ustawienie właściwości `ClientCredentialType` dowolnego obiektu zabezpieczeń transportu (takiego jak <xref:System.ServiceModel.HttpTransportSecurity>) jest ignorowane.</span><span class="sxs-lookup"><span data-stu-id="59e8e-144">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="59e8e-145">Innymi słowy, można ustawić tylko `ClientCredentialType` obiektu zabezpieczeń wiadomości (dla powiązania `WSHttpBinding`, obiektu <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>).</span><span class="sxs-lookup"><span data-stu-id="59e8e-145">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>

<span data-ttu-id="59e8e-146">Aby uzyskać więcej informacji, zobacz [jak: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów](./feature-details/how-to-use-transport-security-and-message-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="59e8e-146">For more information, see [How to: Use Transport Security and Message Credentials](./feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="59e8e-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59e8e-147">See also</span></span>

- [<span data-ttu-id="59e8e-148">Instrukcje: konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="59e8e-148">How to: Configure a Port with an SSL Certificate</span></span>](./feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="59e8e-149">Instrukcje: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="59e8e-149">How to: Use Transport Security and Message Credentials</span></span>](./feature-details/how-to-use-transport-security-and-message-credentials.md)
- [<span data-ttu-id="59e8e-150">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="59e8e-150">Transport Security</span></span>](./feature-details/transport-security.md)
- [<span data-ttu-id="59e8e-151">Zabezpieczenia komunikatów</span><span class="sxs-lookup"><span data-stu-id="59e8e-151">Message Security</span></span>](./feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="59e8e-152">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="59e8e-152">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="59e8e-153">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="59e8e-153">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [<span data-ttu-id="59e8e-154">@no__t — 1security ></span><span class="sxs-lookup"><span data-stu-id="59e8e-154">\<security></span></span>](../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [<span data-ttu-id="59e8e-155">@no__t — 1security ></span><span class="sxs-lookup"><span data-stu-id="59e8e-155">\<security></span></span>](../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [<span data-ttu-id="59e8e-156">@no__t — 1security ></span><span class="sxs-lookup"><span data-stu-id="59e8e-156">\<security></span></span>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
