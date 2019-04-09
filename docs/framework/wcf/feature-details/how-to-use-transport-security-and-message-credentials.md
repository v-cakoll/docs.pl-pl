---
title: 'Instrukcje: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: ea57012f9c09394824b7dbf919930c22fc17bd3d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186817"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="f7c14-102">Instrukcje: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="f7c14-102">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="f7c14-103">Zabezpieczanie usługi za pomocą transportu i komunikat poświadczeń używa najlepsze tryby zabezpieczeń transportu i komunikatów w Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f7c14-103">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="f7c14-104">W sum zabezpieczeń warstwy transportu zapewnia integralności i poufności, podczas komunikat warstwy zabezpieczeń zawiera szereg poświadczenia, które nie są możliwe za pomocą mechanizmów zabezpieczeń transportu strict.</span><span class="sxs-lookup"><span data-stu-id="f7c14-104">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="f7c14-105">W tym temacie przedstawiono podstawowe kroki implementacji transportu przy użyciu poświadczeń komunikatów za pomocą <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.NetTcpBinding> powiązania.</span><span class="sxs-lookup"><span data-stu-id="f7c14-105">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> <span data-ttu-id="f7c14-106">Aby uzyskać więcej informacji na temat ustawiania trybu zabezpieczeń, zobacz [jak: Ustawianie trybu zabezpieczeń](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="f7c14-106">For more information about setting the security mode, see [How to: Set the Security Mode](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="f7c14-107">Podczas ustawiania trybu zabezpieczeń na `TransportWithMessageCredential`, transportu określa konkretny mechanizm, który zapewnia zabezpieczenia na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="f7c14-107">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="f7c14-108">Dla protokołu HTTP mechanizm jest Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP (HTTPS); TCP jest protokół SSL za pośrednictwem protokołu TCP lub Windows.</span><span class="sxs-lookup"><span data-stu-id="f7c14-108">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="f7c14-109">W przypadku transportu HTTP (przy użyciu <xref:System.ServiceModel.WSHttpBinding>), protokołu SSL za pośrednictwem protokołu HTTP zapewnia zabezpieczenia na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="f7c14-109">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="f7c14-110">W takim przypadku należy skonfigurować komputer obsługujący usługę za pomocą certyfikatu SSL powiązany z portem, jak pokazano w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f7c14-110">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="f7c14-111">W przypadku transportu TCP (przy użyciu <xref:System.ServiceModel.NetTcpBinding>), domyślnie podane zabezpieczeń na poziomie transportu jest zabezpieczeń Windows lub protokołu SSL za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="f7c14-111">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="f7c14-112">Przy użyciu protokołu SSL za pośrednictwem protokołu TCP, należy określić certyfikat przy użyciu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodzie, jak pokazano w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f7c14-112">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="f7c14-113">Za pomocą powiązanie WSHttpBinding certyfikat zabezpieczeń transportu (w kodzie)</span><span class="sxs-lookup"><span data-stu-id="f7c14-113">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="f7c14-114">Użyj narzędzia HttpCfg.exe można powiązać certyfikatu SSL z portem na maszynie.</span><span class="sxs-lookup"><span data-stu-id="f7c14-114">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> <span data-ttu-id="f7c14-115">Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="f7c14-115">For more information, see [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2.  <span data-ttu-id="f7c14-116">Utwórz wystąpienie obiektu <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> właściwość <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="f7c14-116">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3.  <span data-ttu-id="f7c14-117">Ustaw <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> właściwość do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="f7c14-117">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="f7c14-118">(Aby uzyskać więcej informacji, zobacz [Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartość.</span><span class="sxs-lookup"><span data-stu-id="f7c14-118">(For more information, see [Selecting a Credential Type](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4.  <span data-ttu-id="f7c14-119">Utwórz wystąpienie obiektu <xref:System.Uri> klasy przy użyciu odpowiedniego adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="f7c14-119">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="f7c14-120">Należy pamiętać, że adres musi używać schematu "HTTPS" i musi zawierać rzeczywista nazwa komputera i numer portu, który certyfikat SSL jest powiązany z.</span><span class="sxs-lookup"><span data-stu-id="f7c14-120">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="f7c14-121">(Ewentualnie można ustawić adres podstawowy w konfiguracji.)</span><span class="sxs-lookup"><span data-stu-id="f7c14-121">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5.  <span data-ttu-id="f7c14-122">Dodawanie punktu końcowego usługi za pomocą <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f7c14-122">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6.  <span data-ttu-id="f7c14-123">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> i wywołać <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodzie, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f7c14-123">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="f7c14-124">Do użytku z certyfikatem zabezpieczeń transportu (w kodzie) NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="f7c14-124">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="f7c14-125">Utwórz wystąpienie obiektu <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> właściwość <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="f7c14-125">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2.  <span data-ttu-id="f7c14-126">Ustaw <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="f7c14-126">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="f7c14-127">Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartość.</span><span class="sxs-lookup"><span data-stu-id="f7c14-127">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3.  <span data-ttu-id="f7c14-128">Utwórz wystąpienie obiektu <xref:System.Uri> klasy przy użyciu odpowiedniego adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="f7c14-128">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="f7c14-129">Należy pamiętać, że adres musi używać schematu "net.tcp".</span><span class="sxs-lookup"><span data-stu-id="f7c14-129">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="f7c14-130">(Ewentualnie można ustawić adres podstawowy w konfiguracji.)</span><span class="sxs-lookup"><span data-stu-id="f7c14-130">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4.  <span data-ttu-id="f7c14-131">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy.</span><span class="sxs-lookup"><span data-stu-id="f7c14-131">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5.  <span data-ttu-id="f7c14-132">Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy, aby jawnie ustawić certyfikat X.509 dla usługi.</span><span class="sxs-lookup"><span data-stu-id="f7c14-132">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6.  <span data-ttu-id="f7c14-133">Dodawanie punktu końcowego usługi za pomocą <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f7c14-133">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7.  <span data-ttu-id="f7c14-134">Wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodzie, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f7c14-134">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="f7c14-135">Za pomocą NetTcpBinding Windows zabezpieczeń transportu (w kodzie)</span><span class="sxs-lookup"><span data-stu-id="f7c14-135">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="f7c14-136">Utwórz wystąpienie obiektu <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> właściwość <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="f7c14-136">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2.  <span data-ttu-id="f7c14-137">Ustawienia zabezpieczeń transportu do użycia Windows, ustawiając <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> do <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="f7c14-137">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="f7c14-138">(Zwróć uwagę, że jest to opcja domyślna).</span><span class="sxs-lookup"><span data-stu-id="f7c14-138">(Note that this is the default.)</span></span>  
  
3.  <span data-ttu-id="f7c14-139">Ustaw <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="f7c14-139">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="f7c14-140">Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartość.</span><span class="sxs-lookup"><span data-stu-id="f7c14-140">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4.  <span data-ttu-id="f7c14-141">Utwórz wystąpienie obiektu <xref:System.Uri> klasy przy użyciu odpowiedniego adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="f7c14-141">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="f7c14-142">Należy pamiętać, że adres musi używać schematu "net.tcp".</span><span class="sxs-lookup"><span data-stu-id="f7c14-142">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="f7c14-143">(Ewentualnie można ustawić adres podstawowy w konfiguracji.)</span><span class="sxs-lookup"><span data-stu-id="f7c14-143">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5.  <span data-ttu-id="f7c14-144">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy.</span><span class="sxs-lookup"><span data-stu-id="f7c14-144">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6.  <span data-ttu-id="f7c14-145">Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy, aby jawnie ustawić certyfikat X.509 dla usługi.</span><span class="sxs-lookup"><span data-stu-id="f7c14-145">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7.  <span data-ttu-id="f7c14-146">Dodawanie punktu końcowego usługi za pomocą <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f7c14-146">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8.  <span data-ttu-id="f7c14-147">Wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodzie, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f7c14-147">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="f7c14-148">Przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f7c14-148">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="f7c14-149">Aby użyć powiązanie WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f7c14-149">To use the WSHttpBinding</span></span>  
  
1.  <span data-ttu-id="f7c14-150">Skonfiguruj komputer tak, za pomocą certyfikatu SSL powiązany z portem.</span><span class="sxs-lookup"><span data-stu-id="f7c14-150">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="f7c14-151">(Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)).</span><span class="sxs-lookup"><span data-stu-id="f7c14-151">(For more information, see [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="f7c14-152">Nie należy ustawić <`transport`> Wartość elementu w przypadku tej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f7c14-152">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2.  <span data-ttu-id="f7c14-153">Określanie typu poświadczeń klienta dla zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f7c14-153">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="f7c14-154">Poniższy przykład ustawia `clientCredentialType` atrybut <`message`> elementu `UserName`.</span><span class="sxs-lookup"><span data-stu-id="f7c14-154">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="f7c14-155">Do użytku z certyfikatem zabezpieczeń transportu NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="f7c14-155">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1.  <span data-ttu-id="f7c14-156">Dla protokołu SSL za pośrednictwem protokołu TCP, należy jawnie określić certyfikat w `<behaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f7c14-156">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="f7c14-157">W poniższym przykładzie określono przez jego wystawcę certyfikatu w domyślnej lokalizacji magazynu (komputer lokalny i magazynów osobistych).</span><span class="sxs-lookup"><span data-stu-id="f7c14-157">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  <span data-ttu-id="f7c14-158">Dodaj [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) do sekcji powiązania</span><span class="sxs-lookup"><span data-stu-id="f7c14-158">Add a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3.  <span data-ttu-id="f7c14-159">Dodaj element powiązania i ustaw `name` atrybutu do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="f7c14-159">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4.  <span data-ttu-id="f7c14-160">Dodaj <`security`> element, a następnie ustaw `mode` atrybutu `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="f7c14-160">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5.  <span data-ttu-id="f7c14-161">Dodaj <`message>` elementu, a następnie ustaw `clientCredentialType` atrybutu do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="f7c14-161">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="f7c14-162">Za pomocą NetTcpBinding Windows zabezpieczeń transportu</span><span class="sxs-lookup"><span data-stu-id="f7c14-162">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1.  <span data-ttu-id="f7c14-163">Dodaj [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) do sekcji powiązania</span><span class="sxs-lookup"><span data-stu-id="f7c14-163">Add a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2.  <span data-ttu-id="f7c14-164">Dodaj <`binding`> element i ustaw `name` atrybutu do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="f7c14-164">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="f7c14-165">Dodaj <`security`> element, a następnie ustaw `mode` atrybutu `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="f7c14-165">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4.  <span data-ttu-id="f7c14-166">Dodaj <`transport`> element i ustaw `clientCredentialType` atrybutu `Windows`.</span><span class="sxs-lookup"><span data-stu-id="f7c14-166">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5.  <span data-ttu-id="f7c14-167">Dodaj <`message`> element i ustaw `clientCredentialType` atrybutu do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="f7c14-167">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="f7c14-168">Poniższy kod ustawia wartość do certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="f7c14-168">The following code sets the value to a certificate.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f7c14-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7c14-169">See also</span></span>

- [<span data-ttu-id="f7c14-170">Instrukcje: Ustawianie trybu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="f7c14-170">How to: Set the Security Mode</span></span>](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)
- [<span data-ttu-id="f7c14-171">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="f7c14-171">Securing Services</span></span>](../../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="f7c14-172">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="f7c14-172">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
