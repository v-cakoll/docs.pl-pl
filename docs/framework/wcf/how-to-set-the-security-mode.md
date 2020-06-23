---
title: 'Instrukcje: Ustawianie trybu zabezpieczeń'
description: 'Dowiedz się, jak ustawić trzy popularne tryby zabezpieczeń WCF dla większości wstępnie zdefiniowanych powiązań: transport, Message i TransportWithMessageCredential.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: 2f834e1930b7676592f6cbc29a577424d75ebc01
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244546"
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="1aac5-103">Instrukcje: Ustawianie trybu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="1aac5-103">How to: Set the Security Mode</span></span>

<span data-ttu-id="1aac5-104">Zabezpieczenia Windows Communication Foundation (WCF) mają trzy popularne tryby zabezpieczeń, które znajdują się w większości wstępnie zdefiniowanych powiązań: transport, Message i "transport z poświadczeniami wiadomości".</span><span class="sxs-lookup"><span data-stu-id="1aac5-104">Windows Communication Foundation (WCF) security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="1aac5-105">Dwa dodatkowe tryby są specyficzne dla dwóch powiązań: tryb "transport-Credential Only" znaleziony w <xref:System.ServiceModel.BasicHttpBinding> i tryb "oba", który znajduje się w <xref:System.ServiceModel.NetMsmqBinding> .</span><span class="sxs-lookup"><span data-stu-id="1aac5-105">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="1aac5-106">Jednak ten temat koncentruje się na trzech wspólnych trybach zabezpieczeń: <xref:System.ServiceModel.SecurityMode.Transport> , <xref:System.ServiceModel.SecurityMode.Message> i <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="1aac5-106">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>

<span data-ttu-id="1aac5-107">Należy zauważyć, że nie każde wstępnie zdefiniowane powiązanie obsługuje wszystkie te tryby.</span><span class="sxs-lookup"><span data-stu-id="1aac5-107">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="1aac5-108">W tym temacie opisano tryb przy użyciu <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.NetTcpBinding> klas i i pokazano, jak ustawić tryb programowo i za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1aac5-108">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>

<span data-ttu-id="1aac5-109">Aby uzyskać więcej informacji, zobacz zabezpieczenia WCF, zobacz [Omówienie zabezpieczeń](./feature-details/security-overview.md), [Zabezpieczanie usług](securing-services.md)i [Zabezpieczanie usług i klientów](./feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="1aac5-109">For more information, see WCF security, see [Security Overview](./feature-details/security-overview.md), [Securing Services](securing-services.md), and [Securing Services and Clients](./feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="1aac5-110">Aby uzyskać więcej informacji na temat trybu transportu i komunikatu, zobacz [zabezpieczenia transportu](./feature-details/transport-security.md) i [zabezpieczenia komunikatów](./feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="1aac5-110">For more information about transport mode and message, see [Transport Security](./feature-details/transport-security.md) and [Message Security](./feature-details/message-security-in-wcf.md).</span></span>

## <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="1aac5-111">Aby ustawić tryb zabezpieczeń w kodzie</span><span class="sxs-lookup"><span data-stu-id="1aac5-111">To set the security mode in code</span></span>

1. <span data-ttu-id="1aac5-112">Utwórz wystąpienie klasy powiązania, której używasz.</span><span class="sxs-lookup"><span data-stu-id="1aac5-112">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="1aac5-113">Aby uzyskać listę wstępnie zdefiniowanych powiązań, zobacz [powiązania dostarczone przez system](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="1aac5-113">For a list of predefined bindings, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="1aac5-114">Ten przykład tworzy wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="1aac5-114">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

2. <span data-ttu-id="1aac5-115">Ustaw `Mode` właściwość obiektu zwróconego przez `Security` Właściwość.</span><span class="sxs-lookup"><span data-stu-id="1aac5-115">Set the `Mode` property of the object returned by the `Security` property.</span></span>

     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]

     <span data-ttu-id="1aac5-116">Alternatywnie można ustawić tryb na komunikat, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1aac5-116">Alternatively, set the mode to message, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]

     <span data-ttu-id="1aac5-117">Lub ustaw tryb transportu z poświadczeniami wiadomości, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1aac5-117">Or set the mode to transport with message credentials, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]

3. <span data-ttu-id="1aac5-118">Można również ustawić tryb w konstruktorze powiązania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1aac5-118">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]

## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="1aac5-119">Ustawianie właściwości ClientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="1aac5-119">Setting the ClientCredentialType Property</span></span>

<span data-ttu-id="1aac5-120">Ustawienie trybu na jedną z trzech wartości określa sposób ustawiania `ClientCredentialType` właściwości.</span><span class="sxs-lookup"><span data-stu-id="1aac5-120">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="1aac5-121">Na przykład przy użyciu <xref:System.ServiceModel.WSHttpBinding> klasy, ustawienie trybu na `Transport` oznacza, że należy ustawić <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> Właściwość <xref:System.ServiceModel.HttpTransportSecurity> klasy na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="1aac5-121">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="1aac5-122">Aby ustawić właściwość ClientCredentialtype dla trybu transportu</span><span class="sxs-lookup"><span data-stu-id="1aac5-122">To set the ClientCredentialType property for Transport mode</span></span>

1. <span data-ttu-id="1aac5-123">Utwórz wystąpienie powiązania.</span><span class="sxs-lookup"><span data-stu-id="1aac5-123">Create an instance of the binding.</span></span>

2. <span data-ttu-id="1aac5-124">Ustaw `Mode` Właściwość na wartość `Transport` .</span><span class="sxs-lookup"><span data-stu-id="1aac5-124">Set the `Mode` property to `Transport`.</span></span>

3. <span data-ttu-id="1aac5-125">Ustaw `ClientCredential` Właściwość na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="1aac5-125">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="1aac5-126">Poniższy kod ustawia właściwość na `Windows` .</span><span class="sxs-lookup"><span data-stu-id="1aac5-126">The following code sets the property to `Windows`.</span></span>

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="1aac5-127">Aby ustawić właściwość ClientCredentialtype dla trybu komunikatu</span><span class="sxs-lookup"><span data-stu-id="1aac5-127">To set the ClientCredentialType property for Message mode</span></span>

1. <span data-ttu-id="1aac5-128">Utwórz wystąpienie powiązania.</span><span class="sxs-lookup"><span data-stu-id="1aac5-128">Create an instance of the binding.</span></span>

2. <span data-ttu-id="1aac5-129">Ustaw `Mode` Właściwość na wartość `Message` .</span><span class="sxs-lookup"><span data-stu-id="1aac5-129">Set the `Mode` property to `Message`.</span></span>

3. <span data-ttu-id="1aac5-130">Ustaw `ClientCredential` Właściwość na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="1aac5-130">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="1aac5-131">Poniższy kod ustawia właściwość na `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="1aac5-131">The following code sets the property to `Certificate`.</span></span>

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="1aac5-132">Aby ustawić tryb i Właściwość ClientCredentialtype w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1aac5-132">To set the Mode and ClientCredentialType property in configuration</span></span>

1. <span data-ttu-id="1aac5-133">Dodaj odpowiedni element powiązania do elementu w [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1aac5-133">Add an appropriate binding element to the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="1aac5-134">Poniższy przykład dodaje [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="1aac5-134">The following example adds a [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

2. <span data-ttu-id="1aac5-135">Dodaj `<binding>` element i ustaw jego `name` atrybut na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="1aac5-135">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="1aac5-136">Dodaj `<security>` element i ustaw `mode` atrybut na `Message` , `Transport` , lub `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="1aac5-136">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

4. <span data-ttu-id="1aac5-137">Jeśli tryb jest ustawiony na `Transport` , Dodaj `<transport>` element i ustaw `clientCredential` odpowiednią wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1aac5-137">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>

     <span data-ttu-id="1aac5-138">Poniższy przykład ustawia tryb na " `Transport"` , a następnie ustawia `clientCredentialType` atrybut `<transport>` elementu na" `Windows"` .</span><span class="sxs-lookup"><span data-stu-id="1aac5-138">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="1aac5-139">Alternatywnie możesz ustawić `security mode` do " `Message"` , po którym następuje `<"message">` element.</span><span class="sxs-lookup"><span data-stu-id="1aac5-139">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="1aac5-140">W tym przykładzie ustawiono wartość `clientCredentialType` " `Certificate"` .</span><span class="sxs-lookup"><span data-stu-id="1aac5-140">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="1aac5-141">Użycie <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> wartości jest szczególnym przypadkiem i wyjaśniono poniżej.</span><span class="sxs-lookup"><span data-stu-id="1aac5-141">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>

### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="1aac5-142">Korzystanie z TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="1aac5-142">Using TransportWithMessageCredential</span></span>

<span data-ttu-id="1aac5-143">Podczas ustawiania trybu zabezpieczeń na `TransportWithMessageCredential` , transport określa rzeczywisty mechanizm, który zapewnia zabezpieczenia na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="1aac5-143">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="1aac5-144">Na przykład protokół HTTP używa protokołu SSL (SSL) za pośrednictwem protokołu HTTP (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="1aac5-144">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="1aac5-145">W związku z tym ustawienie `ClientCredentialType` właściwości dowolnego obiektu zabezpieczeń transportu (takiego jak <xref:System.ServiceModel.HttpTransportSecurity> ) jest ignorowane.</span><span class="sxs-lookup"><span data-stu-id="1aac5-145">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="1aac5-146">Innymi słowy, można ustawić tylko `ClientCredentialType` obiekt zabezpieczeń wiadomości (dla `WSHttpBinding` powiązania, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> obiekt).</span><span class="sxs-lookup"><span data-stu-id="1aac5-146">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>

<span data-ttu-id="1aac5-147">Aby uzyskać więcej informacji, zobacz [jak: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów](./feature-details/how-to-use-transport-security-and-message-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="1aac5-147">For more information, see [How to: Use Transport Security and Message Credentials](./feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1aac5-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1aac5-148">See also</span></span>

- [<span data-ttu-id="1aac5-149">Instrukcje: konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="1aac5-149">How to: Configure a Port with an SSL Certificate</span></span>](./feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="1aac5-150">Instrukcje: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="1aac5-150">How to: Use Transport Security and Message Credentials</span></span>](./feature-details/how-to-use-transport-security-and-message-credentials.md)
- [<span data-ttu-id="1aac5-151">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="1aac5-151">Transport Security</span></span>](./feature-details/transport-security.md)
- [<span data-ttu-id="1aac5-152">Zabezpieczenia komunikatów</span><span class="sxs-lookup"><span data-stu-id="1aac5-152">Message Security</span></span>](./feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="1aac5-153">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="1aac5-153">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="1aac5-154">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="1aac5-154">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
