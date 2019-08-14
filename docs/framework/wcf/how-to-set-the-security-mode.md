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
ms.openlocfilehash: 6bd81bd24d28f0a9e318d60a3b7fb4aa059f9a49
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971977"
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="68e15-102">Instrukcje: Ustawianie trybu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="68e15-102">How to: Set the Security Mode</span></span>

<span data-ttu-id="68e15-103">Zabezpieczenia Windows Communication Foundation (WCF) mają trzy popularne tryby zabezpieczeń, które znajdują się w większości wstępnie zdefiniowanych powiązań: transport, Message i "transport z poświadczeniami wiadomości".</span><span class="sxs-lookup"><span data-stu-id="68e15-103">Windows Communication Foundation (WCF) security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="68e15-104">Dwa dodatkowe tryby są specyficzne dla dwóch powiązań: tryb "transport-Credential Only" znaleziony w <xref:System.ServiceModel.BasicHttpBinding>i tryb "oba", który znajduje się <xref:System.ServiceModel.NetMsmqBinding>w.</span><span class="sxs-lookup"><span data-stu-id="68e15-104">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="68e15-105">Jednak ten temat koncentruje się na trzech wspólnych trybach zabezpieczeń: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>i <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="68e15-105">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>

<span data-ttu-id="68e15-106">Należy zauważyć, że nie każde wstępnie zdefiniowane powiązanie obsługuje wszystkie te tryby.</span><span class="sxs-lookup"><span data-stu-id="68e15-106">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="68e15-107">W tym temacie opisano tryb przy użyciu <xref:System.ServiceModel.WSHttpBinding> klas <xref:System.ServiceModel.NetTcpBinding> i i pokazano, jak ustawić tryb programowo i za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="68e15-107">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>

<span data-ttu-id="68e15-108">Aby uzyskać więcej informacji, zobacz zabezpieczenia WCF, zobacz [Omówienie zabezpieczeń](../../../docs/framework/wcf/feature-details/security-overview.md), [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)i [Zabezpieczanie usług i klientów](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="68e15-108">For more information, see WCF security, see [Security Overview](../../../docs/framework/wcf/feature-details/security-overview.md), [Securing Services](../../../docs/framework/wcf/securing-services.md), and [Securing Services and Clients](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="68e15-109">Aby uzyskać więcej informacji na temat trybu transportu i komunikatu, zobacz [zabezpieczenia transportu](../../../docs/framework/wcf/feature-details/transport-security.md) i [zabezpieczenia komunikatów](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="68e15-109">For more information about transport mode and message, see [Transport Security](../../../docs/framework/wcf/feature-details/transport-security.md) and [Message Security](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>

## <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="68e15-110">Aby ustawić tryb zabezpieczeń w kodzie</span><span class="sxs-lookup"><span data-stu-id="68e15-110">To set the security mode in code</span></span>

1. <span data-ttu-id="68e15-111">Utwórz wystąpienie klasy powiązania, której używasz.</span><span class="sxs-lookup"><span data-stu-id="68e15-111">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="68e15-112">Aby uzyskać listę wstępnie zdefiniowanych powiązań, zobacz [powiązania dostarczone przez system](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="68e15-112">For a list of predefined bindings, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="68e15-113">Ten przykład tworzy wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="68e15-113">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

2. <span data-ttu-id="68e15-114">Ustaw właściwość obiektu zwróconego `Security` przez właściwość. `Mode`</span><span class="sxs-lookup"><span data-stu-id="68e15-114">Set the `Mode` property of the object returned by the `Security` property.</span></span>

     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]

     <span data-ttu-id="68e15-115">Alternatywnie można ustawić tryb na komunikat, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="68e15-115">Alternatively, set the mode to message, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]

     <span data-ttu-id="68e15-116">Lub ustaw tryb transportu z poświadczeniami wiadomości, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="68e15-116">Or set the mode to transport with message credentials, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]

3. <span data-ttu-id="68e15-117">Można również ustawić tryb w konstruktorze powiązania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="68e15-117">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]

## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="68e15-118">Ustawianie właściwości ClientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="68e15-118">Setting the ClientCredentialType Property</span></span>

<span data-ttu-id="68e15-119">Ustawienie trybu na jedną z trzech wartości określa sposób ustawiania `ClientCredentialType` właściwości.</span><span class="sxs-lookup"><span data-stu-id="68e15-119">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="68e15-120">Na <xref:System.ServiceModel.WSHttpBinding> przykład przy użyciu klasy, ustawienie trybu na `Transport` <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> oznacza, że należy <xref:System.ServiceModel.HttpTransportSecurity> ustawić właściwość klasy na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="68e15-120">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="68e15-121">Aby ustawić właściwość ClientCredentialtype dla trybu transportu</span><span class="sxs-lookup"><span data-stu-id="68e15-121">To set the ClientCredentialType property for Transport mode</span></span>

1. <span data-ttu-id="68e15-122">Utwórz wystąpienie powiązania.</span><span class="sxs-lookup"><span data-stu-id="68e15-122">Create an instance of the binding.</span></span>

2. <span data-ttu-id="68e15-123">Ustaw `Mode` właściwość `Transport`.</span><span class="sxs-lookup"><span data-stu-id="68e15-123">Set the `Mode` property to `Transport`.</span></span>

3. <span data-ttu-id="68e15-124">`ClientCredential` Ustaw właściwość na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="68e15-124">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="68e15-125">Poniższy kod ustawia właściwość na `Windows`.</span><span class="sxs-lookup"><span data-stu-id="68e15-125">The following code sets the property to `Windows`.</span></span>

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="68e15-126">Aby ustawić właściwość ClientCredentialtype dla trybu komunikatu</span><span class="sxs-lookup"><span data-stu-id="68e15-126">To set the ClientCredentialType property for Message mode</span></span>

1. <span data-ttu-id="68e15-127">Utwórz wystąpienie powiązania.</span><span class="sxs-lookup"><span data-stu-id="68e15-127">Create an instance of the binding.</span></span>

2. <span data-ttu-id="68e15-128">Ustaw `Mode` właściwość `Message`.</span><span class="sxs-lookup"><span data-stu-id="68e15-128">Set the `Mode` property to `Message`.</span></span>

3. <span data-ttu-id="68e15-129">`ClientCredential` Ustaw właściwość na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="68e15-129">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="68e15-130">Poniższy kod ustawia właściwość na `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="68e15-130">The following code sets the property to `Certificate`.</span></span>

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="68e15-131">Aby ustawić tryb i Właściwość ClientCredentialtype w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="68e15-131">To set the Mode and ClientCredentialType property in configuration</span></span>

1. <span data-ttu-id="68e15-132">Dodaj odpowiedni element powiązania do [ \<elementu powiązań >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="68e15-132">Add an appropriate binding element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="68e15-133">Poniższy przykład dodaje [ \<element > WSHttpBinding](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="68e15-133">The following example adds a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

2. <span data-ttu-id="68e15-134">Dodaj element i ustaw jego `name` atrybut na odpowiednią wartość. `<binding>`</span><span class="sxs-lookup"><span data-stu-id="68e15-134">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="68e15-135">`mode` `Message`Dodaj element i ustaw atrybut na, `Transport`, lub `TransportWithMessageCredential`. `<security>`</span><span class="sxs-lookup"><span data-stu-id="68e15-135">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

4. <span data-ttu-id="68e15-136">Jeśli tryb jest ustawiony na `Transport`, `<transport>` Dodaj element i ustaw `clientCredential` odpowiednią wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="68e15-136">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>

     <span data-ttu-id="68e15-137">Poniższy przykład`Transport"`ustawia tryb na ", a następnie `clientCredentialType` ustawia atrybut `<transport>` elementu na"`Windows"`.</span><span class="sxs-lookup"><span data-stu-id="68e15-137">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="68e15-138">Alternatywnie możesz ustawić `security mode` do "`Message"`, po którym następuje `<"message">` element.</span><span class="sxs-lookup"><span data-stu-id="68e15-138">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="68e15-139">W tym przykładzie ustawiono `clientCredentialType` wartość "`Certificate"`.</span><span class="sxs-lookup"><span data-stu-id="68e15-139">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="68e15-140"><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> Użycie wartości jest szczególnym przypadkiem i wyjaśniono poniżej.</span><span class="sxs-lookup"><span data-stu-id="68e15-140">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>

### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="68e15-141">Korzystanie z TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="68e15-141">Using TransportWithMessageCredential</span></span>

<span data-ttu-id="68e15-142">Podczas ustawiania trybu zabezpieczeń na `TransportWithMessageCredential`, transport określa rzeczywisty mechanizm, który zapewnia zabezpieczenia na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="68e15-142">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="68e15-143">Na przykład protokół HTTP używa protokołu SSL (SSL) za pośrednictwem protokołu HTTP (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="68e15-143">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="68e15-144">W związku z tym `ClientCredentialType` ustawienie właściwości dowolnego obiektu zabezpieczeń transportu (takiego jak <xref:System.ServiceModel.HttpTransportSecurity>) jest ignorowane.</span><span class="sxs-lookup"><span data-stu-id="68e15-144">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="68e15-145">Innymi słowy, można ustawić `ClientCredentialType` tylko obiekt zabezpieczeń wiadomości ( `WSHttpBinding` dla powiązania, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> obiekt).</span><span class="sxs-lookup"><span data-stu-id="68e15-145">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>

<span data-ttu-id="68e15-146">Aby uzyskać więcej informacji, zobacz [jak: Użyj zabezpieczeń transportu i poświadczeń](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)komunikatów.</span><span class="sxs-lookup"><span data-stu-id="68e15-146">For more information, see [How to: Use Transport Security and Message Credentials](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="68e15-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68e15-147">See also</span></span>

- [<span data-ttu-id="68e15-148">Instrukcje: Konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="68e15-148">How to: Configure a Port with an SSL Certificate</span></span>](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="68e15-149">Instrukcje: Korzystanie z zabezpieczeń transportu i poświadczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="68e15-149">How to: Use Transport Security and Message Credentials</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)
- [<span data-ttu-id="68e15-150">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="68e15-150">Transport Security</span></span>](../../../docs/framework/wcf/feature-details/transport-security.md)
- [<span data-ttu-id="68e15-151">Zabezpieczenia komunikatów</span><span class="sxs-lookup"><span data-stu-id="68e15-151">Message Security</span></span>](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="68e15-152">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="68e15-152">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="68e15-153">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="68e15-153">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="68e15-154">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="68e15-154">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [<span data-ttu-id="68e15-155">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="68e15-155">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [<span data-ttu-id="68e15-156">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="68e15-156">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
