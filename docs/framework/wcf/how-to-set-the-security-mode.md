---
title: 'Instrukcje: Ustawianie trybu zabezpieczeń'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
caps.latest.revision: 22
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 34c53389694aa48742becfd713796feb8111d888
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="d7e78-102">Instrukcje: Ustawianie trybu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d7e78-102">How to: Set the Security Mode</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="d7e78-103"> zabezpieczenia mają trzy często używanych trybów zabezpieczeń, które zostały znalezione na najbardziej wstępnie zdefiniowanych powiązań: transportu, komunikat oraz "transportu z poświadczeniami komunikatu".</span><span class="sxs-lookup"><span data-stu-id="d7e78-103"> security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="d7e78-104">Dwa tryby dodatkowe są specyficzne dla dwa powiązania: tryb "tylko transportu credential" znaleziono na <xref:System.ServiceModel.BasicHttpBinding>oraz "Zarówno" tryb na <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="d7e78-104">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="d7e78-105">Jednak ten temat koncentruje się na trzech często używanych trybów zabezpieczeń: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, i <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="d7e78-105">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
 <span data-ttu-id="d7e78-106">Zauważ, że nie wszystkie wstępnie zdefiniowanych powiązań obsługuje wszystkie te tryby.</span><span class="sxs-lookup"><span data-stu-id="d7e78-106">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="d7e78-107">W tym temacie Ustawia tryb z <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.NetTcpBinding> klas i pokazuje, jak ustawić tryb programowo i za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d7e78-107">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>  
  
 <span data-ttu-id="d7e78-108">Aby uzyskać więcej informacji, zobacz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zabezpieczeń, zobacz [Omówienie zabezpieczeń](../../../docs/framework/wcf/feature-details/security-overview.md), [zabezpieczania usług](../../../docs/framework/wcf/securing-services.md), i [zabezpieczanie usług i klientów](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="d7e78-108">For more information, see [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] security, see [Security Overview](../../../docs/framework/wcf/feature-details/security-overview.md), [Securing Services](../../../docs/framework/wcf/securing-services.md), and [Securing Services and Clients](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="d7e78-109"> transport trybu i komunikatów, zobacz [zabezpieczeń transportu](../../../docs/framework/wcf/feature-details/transport-security.md) i [zabezpieczenia komunikatów](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="d7e78-109"> transport mode and message, see [Transport Security](../../../docs/framework/wcf/feature-details/transport-security.md) and [Message Security](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
### <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="d7e78-110">Aby ustawić tryb zabezpieczeń w kodzie</span><span class="sxs-lookup"><span data-stu-id="d7e78-110">To set the security mode in code</span></span>  
  
1.  <span data-ttu-id="d7e78-111">Tworzenie wystąpienia klasy powiązanie, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="d7e78-111">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="d7e78-112">Aby uzyskać listę wstępnie zdefiniowanych powiązań, zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="d7e78-112">For a list of predefined bindings, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="d7e78-113">W tym przykładzie powoduje utworzenie wystąpienia <xref:System.ServiceModel.WSHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="d7e78-113">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>  
  
2.  <span data-ttu-id="d7e78-114">Ustaw `Mode` właściwości obiektu zwróconego przez `Security` właściwości.</span><span class="sxs-lookup"><span data-stu-id="d7e78-114">Set the `Mode` property of the object returned by the `Security` property.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     <span data-ttu-id="d7e78-115">Możesz również ustawić tryb na wiadomość, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d7e78-115">Alternatively, set the mode to message, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     <span data-ttu-id="d7e78-116">Lub ustaw tryb transportu z poświadczeniami komunikatu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d7e78-116">Or set the mode to transport with message credentials, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3.  <span data-ttu-id="d7e78-117">Tryb można również ustawić w Konstruktorze powiązanie, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d7e78-117">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="d7e78-118">Ustawienie właściwości ClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="d7e78-118">Setting the ClientCredentialType Property</span></span>  
 <span data-ttu-id="d7e78-119">Ustawianie trybu do jednej z następujących wartości: Określa, jak ustawić `ClientCredentialType` właściwości.</span><span class="sxs-lookup"><span data-stu-id="d7e78-119">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="d7e78-120">Na przykład za pomocą <xref:System.ServiceModel.WSHttpBinding> klasy ustawienie trybu `Transport` oznacza, że należy ustawić <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> właściwość <xref:System.ServiceModel.HttpTransportSecurity> klasy odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="d7e78-120">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>  
  
#### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="d7e78-121">Można ustawić właściwości ClientCredentialType dla trybu transportu</span><span class="sxs-lookup"><span data-stu-id="d7e78-121">To set the ClientCredentialType property for Transport mode</span></span>  
  
1.  <span data-ttu-id="d7e78-122">Utwórz wystąpienie powiązania.</span><span class="sxs-lookup"><span data-stu-id="d7e78-122">Create an instance of the binding.</span></span>  
  
2.  <span data-ttu-id="d7e78-123">Ustaw `Mode` właściwości `Transport`.</span><span class="sxs-lookup"><span data-stu-id="d7e78-123">Set the `Mode` property to `Transport`.</span></span>  
  
3.  <span data-ttu-id="d7e78-124">Ustaw `ClientCredential` właściwości odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="d7e78-124">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="d7e78-125">Poniższy kod ustawia właściwość `Windows`.</span><span class="sxs-lookup"><span data-stu-id="d7e78-125">The following code sets the property to `Windows`.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="d7e78-126">Można ustawić właściwości ClientCredentialType dla trybu wiadomości</span><span class="sxs-lookup"><span data-stu-id="d7e78-126">To set the ClientCredentialType property for Message mode</span></span>  
  
1.  <span data-ttu-id="d7e78-127">Utwórz wystąpienie powiązania.</span><span class="sxs-lookup"><span data-stu-id="d7e78-127">Create an instance of the binding.</span></span>  
  
2.  <span data-ttu-id="d7e78-128">Ustaw `Mode` właściwości `Message`.</span><span class="sxs-lookup"><span data-stu-id="d7e78-128">Set the `Mode` property to `Message`.</span></span>  
  
3.  <span data-ttu-id="d7e78-129">Ustaw `ClientCredential` właściwości odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="d7e78-129">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="d7e78-130">Poniższy kod ustawia właściwość `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="d7e78-130">The following code sets the property to `Certificate`.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="d7e78-131">Aby ustawić właściwość trybu i ClientCredentialType w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d7e78-131">To set the Mode and ClientCredentialType property in configuration</span></span>  
  
1.  <span data-ttu-id="d7e78-132">Dodaj odpowiednie powiązanie elementu [ \<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d7e78-132">Add an appropriate binding element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="d7e78-133">W poniższym przykładzie dodano [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d7e78-133">The following example adds a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
2.  <span data-ttu-id="d7e78-134">Dodaj `<binding>` element i ustaw jej `name` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="d7e78-134">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="d7e78-135">Dodaj `<security>` element i ustaw `mode` atrybutu `Message`, `Transport`, lub `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="d7e78-135">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>  
  
4.  <span data-ttu-id="d7e78-136">Jeśli ustawiono tryb `Transport`, Dodaj `<transport>` element i ustaw `clientCredential` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="d7e78-136">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>  
  
     <span data-ttu-id="d7e78-137">Poniższy przykład przedstawia sposób "`Transport"`, a następnie ustawia `clientCredentialType` atrybutu `<transport>` elementu"`Windows"`.</span><span class="sxs-lookup"><span data-stu-id="d7e78-137">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" />  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     <span data-ttu-id="d7e78-138">Możesz również ustawić `security mode` do "`Message"`, a następnie `<"message">` elementu.</span><span class="sxs-lookup"><span data-stu-id="d7e78-138">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="d7e78-139">W tym przykładzie `clientCredentialType` do "`Certificate"`.</span><span class="sxs-lookup"><span data-stu-id="d7e78-139">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" />  
           <message clientCredentialType = "Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     <span data-ttu-id="d7e78-140">Przy użyciu <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> wartość jest szczególnych przypadkach i opisanej poniżej.</span><span class="sxs-lookup"><span data-stu-id="d7e78-140">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>  
  
### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="d7e78-141">Przy użyciu TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d7e78-141">Using TransportWithMessageCredential</span></span>  
 <span data-ttu-id="d7e78-142">Podczas ustawiania trybu zabezpieczeń `TransportWithMessageCredential`, transport określa konkretny mechanizm, który zapewnia zabezpieczeń na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="d7e78-142">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="d7e78-143">Na przykład protokołu HTTP używa protokołu Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="d7e78-143">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="d7e78-144">W związku z tym ustawienie `ClientCredentialType` właściwość wszystkich obiektów zabezpieczeń transportu (takich jak <xref:System.ServiceModel.HttpTransportSecurity>) jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="d7e78-144">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="d7e78-145">Innymi słowy, można ustawić tylko `ClientCredentialType` obiektu zabezpieczeń wiadomości (dla `WSHttpBinding` powiązanie, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> obiektu).</span><span class="sxs-lookup"><span data-stu-id="d7e78-145">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>  
  
 <span data-ttu-id="d7e78-146">Aby uzyskać więcej informacji, zobacz [porady: Korzystanie z zabezpieczeń transportu i poświadczeń komunikatów](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="d7e78-146">For more information, see [How to: Use Transport Security and Message Credentials](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7e78-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7e78-147">See Also</span></span>  
 [<span data-ttu-id="d7e78-148">Instrukcje: konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="d7e78-148">How to: Configure a Port with an SSL Certificate</span></span>](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="d7e78-149">Instrukcje: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="d7e78-149">How to: Use Transport Security and Message Credentials</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [<span data-ttu-id="d7e78-150">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="d7e78-150">Transport Security</span></span>](../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="d7e78-151">Zabezpieczenia komunikatów</span><span class="sxs-lookup"><span data-stu-id="d7e78-151">Message Security</span></span>](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [<span data-ttu-id="d7e78-152">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d7e78-152">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="d7e78-153">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="d7e78-153">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="d7e78-154">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="d7e78-154">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)  
 [<span data-ttu-id="d7e78-155">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="d7e78-155">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)  
 [<span data-ttu-id="d7e78-156">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="d7e78-156">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
