---
title: 'Instrukcje: Korzystanie z zabezpieczeń transportu i poświadczeń komunikatów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f49c0eb46141081b91100a5ae1869cbcf556e353
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579387"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="cf008-102">Instrukcje: Korzystanie z zabezpieczeń transportu i poświadczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="cf008-102">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="cf008-103">Zabezpieczanie usługi przy użyciu poświadczeń transportowych i komunikatów jest zgodne z najlepszymi trybami zabezpieczeń transportu i komunikatów w programie Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="cf008-103">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="cf008-104">W obszarze suma zabezpieczenia warstwy transport zapewnia integralność i poufność, natomiast zabezpieczenia warstwy komunikatów zapewniają wiele poświadczeń, które nie są możliwe przy użyciu ścisłych mechanizmów zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="cf008-104">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="cf008-105">W tym temacie przedstawiono podstawowe kroki wdrażania transportu za pomocą poświadczeń przy użyciu <xref:System.ServiceModel.WSHttpBinding> powiązań i <xref:System.ServiceModel.NetTcpBinding> .</span><span class="sxs-lookup"><span data-stu-id="cf008-105">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> <span data-ttu-id="cf008-106">Aby uzyskać więcej informacji na temat ustawiania trybu zabezpieczeń, zobacz [How to: Set a Security Mode](../how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="cf008-106">For more information about setting the security mode, see [How to: Set the Security Mode](../how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="cf008-107">Podczas ustawiania trybu zabezpieczeń na `TransportWithMessageCredential` , transport określa rzeczywisty mechanizm, który zapewnia zabezpieczenia na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="cf008-107">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="cf008-108">W przypadku protokołu HTTP mechanizm jest SSL (SSL) za pośrednictwem protokołu HTTP (HTTPS); w przypadku protokołu TCP jest to protokół SSL za pośrednictwem protokołu TCP lub Windows.</span><span class="sxs-lookup"><span data-stu-id="cf008-108">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="cf008-109">Jeśli transport jest HTTP (przy użyciu <xref:System.ServiceModel.WSHttpBinding> ), protokół SSL za pośrednictwem protokołu HTTP zapewnia zabezpieczenia na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="cf008-109">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="cf008-110">W takim przypadku należy skonfigurować komputer hostujący usługę przy użyciu certyfikatu SSL powiązanego z portem, jak pokazano w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cf008-110">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="cf008-111">Jeśli transport to TCP (przy użyciu programu <xref:System.ServiceModel.NetTcpBinding> ), domyślnie zapewnione zabezpieczenia na poziomie transportu to zabezpieczenia systemu Windows lub SSL za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="cf008-111">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="cf008-112">W przypadku korzystania z protokołu SSL za pośrednictwem protokołu TCP należy określić certyfikat przy użyciu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody, jak pokazano w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cf008-112">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="cf008-113">Aby użyć WSHttpBinding z certyfikatem do zabezpieczenia transportu (w kodzie)</span><span class="sxs-lookup"><span data-stu-id="cf008-113">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="cf008-114">Za pomocą narzędzia HttpCfg. exe Powiąż certyfikat SSL z portem na maszynie.</span><span class="sxs-lookup"><span data-stu-id="cf008-114">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> <span data-ttu-id="cf008-115">Aby uzyskać więcej informacji, zobacz [How to: Configure a port with a SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="cf008-115">For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2. <span data-ttu-id="cf008-116">Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> Właściwość na <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="cf008-116">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3. <span data-ttu-id="cf008-117">Ustaw <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> Właściwość na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="cf008-117">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="cf008-118">(Aby uzyskać więcej informacji, zobacz [Wybieranie typu poświadczeń](selecting-a-credential-type.md)). Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartości.</span><span class="sxs-lookup"><span data-stu-id="cf008-118">(For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="cf008-119">Utwórz wystąpienie <xref:System.Uri> klasy z odpowiednim adresem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="cf008-119">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="cf008-120">Należy pamiętać, że adres musi używać schematu "HTTPS" i musi zawierać rzeczywistą nazwę komputera i numer portu, z którym jest powiązany certyfikat SSL.</span><span class="sxs-lookup"><span data-stu-id="cf008-120">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="cf008-121">(Alternatywnie można ustawić adres podstawowy w konfiguracji).</span><span class="sxs-lookup"><span data-stu-id="cf008-121">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="cf008-122">Dodaj punkt końcowy usługi przy użyciu <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cf008-122">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6. <span data-ttu-id="cf008-123">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> i Wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodę, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="cf008-123">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="cf008-124">Aby użyć NetTcpBinding z certyfikatem do zabezpieczenia transportu (w kodzie)</span><span class="sxs-lookup"><span data-stu-id="cf008-124">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="cf008-125">Utwórz wystąpienie <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> Właściwość na <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="cf008-125">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="cf008-126">Ustaw <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="cf008-126">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="cf008-127">Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartości.</span><span class="sxs-lookup"><span data-stu-id="cf008-127">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3. <span data-ttu-id="cf008-128">Utwórz wystąpienie <xref:System.Uri> klasy z odpowiednim adresem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="cf008-128">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="cf008-129">Należy pamiętać, że adres musi używać schematu "net. TCP".</span><span class="sxs-lookup"><span data-stu-id="cf008-129">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="cf008-130">(Alternatywnie można ustawić adres podstawowy w konfiguracji).</span><span class="sxs-lookup"><span data-stu-id="cf008-130">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4. <span data-ttu-id="cf008-131">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy.</span><span class="sxs-lookup"><span data-stu-id="cf008-131">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5. <span data-ttu-id="cf008-132">Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy, aby jawnie ustawić certyfikat X. 509 dla usługi.</span><span class="sxs-lookup"><span data-stu-id="cf008-132">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6. <span data-ttu-id="cf008-133">Dodaj punkt końcowy usługi przy użyciu <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cf008-133">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7. <span data-ttu-id="cf008-134">Wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodę, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="cf008-134">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="cf008-135">Aby użyć NetTcpBinding z systemem Windows do zabezpieczenia transportu (w kodzie)</span><span class="sxs-lookup"><span data-stu-id="cf008-135">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1. <span data-ttu-id="cf008-136">Utwórz wystąpienie <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> Właściwość na <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="cf008-136">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="cf008-137">Ustaw zabezpieczenia transportu, aby używały systemu Windows przez ustawienie <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> do <xref:System.ServiceModel.TcpClientCredentialType.Windows> .</span><span class="sxs-lookup"><span data-stu-id="cf008-137">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="cf008-138">(Należy zauważyć, że jest to wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="cf008-138">(Note that this is the default.)</span></span>  
  
3. <span data-ttu-id="cf008-139">Ustaw <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="cf008-139">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="cf008-140">Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartości.</span><span class="sxs-lookup"><span data-stu-id="cf008-140">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="cf008-141">Utwórz wystąpienie <xref:System.Uri> klasy z odpowiednim adresem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="cf008-141">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="cf008-142">Należy pamiętać, że adres musi używać schematu "net. TCP".</span><span class="sxs-lookup"><span data-stu-id="cf008-142">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="cf008-143">(Alternatywnie można ustawić adres podstawowy w konfiguracji).</span><span class="sxs-lookup"><span data-stu-id="cf008-143">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="cf008-144">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy.</span><span class="sxs-lookup"><span data-stu-id="cf008-144">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6. <span data-ttu-id="cf008-145">Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy, aby jawnie ustawić certyfikat X. 509 dla usługi.</span><span class="sxs-lookup"><span data-stu-id="cf008-145">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7. <span data-ttu-id="cf008-146">Dodaj punkt końcowy usługi przy użyciu <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cf008-146">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8. <span data-ttu-id="cf008-147">Wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodę, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="cf008-147">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="cf008-148">Korzystanie z konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cf008-148">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="cf008-149">Aby użyć WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="cf008-149">To use the WSHttpBinding</span></span>  
  
1. <span data-ttu-id="cf008-150">Skonfiguruj komputer przy użyciu certyfikatu SSL powiązanego z portem.</span><span class="sxs-lookup"><span data-stu-id="cf008-150">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="cf008-151">(Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie portu z certyfikatem SSL](how-to-configure-a-port-with-an-ssl-certificate.md)).</span><span class="sxs-lookup"><span data-stu-id="cf008-151">(For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="cf008-152">Nie trzeba ustawiać <`transport`> wartości elementu przy użyciu tej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cf008-152">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2. <span data-ttu-id="cf008-153">Określ typ poświadczeń klienta dla zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="cf008-153">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="cf008-154">Poniższy przykład ustawia `clientCredentialType` atrybut <`message` elementu> na `UserName` .</span><span class="sxs-lookup"><span data-stu-id="cf008-154">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="cf008-155">Aby użyć NetTcpBinding z certyfikatem na potrzeby zabezpieczeń transportu</span><span class="sxs-lookup"><span data-stu-id="cf008-155">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1. <span data-ttu-id="cf008-156">W przypadku protokołu SSL za pośrednictwem protokołu TCP należy jawnie określić certyfikat w `<behaviors>` elemencie.</span><span class="sxs-lookup"><span data-stu-id="cf008-156">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="cf008-157">W poniższym przykładzie określono certyfikat wystawcy w domyślnej lokalizacji magazynu (komputer lokalny i magazyny osobiste).</span><span class="sxs-lookup"><span data-stu-id="cf008-157">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
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
  
2. <span data-ttu-id="cf008-158">Dodawanie [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) do sekcji powiązań</span><span class="sxs-lookup"><span data-stu-id="cf008-158">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3. <span data-ttu-id="cf008-159">Dodaj element powiązania i ustaw `name` odpowiednią wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cf008-159">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="cf008-160">Dodaj `security` element> <i ustaw `mode` atrybut na `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="cf008-160">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5. <span data-ttu-id="cf008-161">Dodaj element <`message>` i ustaw `clientCredentialType` odpowiednią wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cf008-161">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
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
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="cf008-162">Aby użyć NetTcpBinding z systemem Windows do zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="cf008-162">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1. <span data-ttu-id="cf008-163">Dodaj [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) do sekcji powiązań,</span><span class="sxs-lookup"><span data-stu-id="cf008-163">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2. <span data-ttu-id="cf008-164">Dodaj `binding` element> <i ustaw `name` odpowiednią wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cf008-164">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="cf008-165">Dodaj `security` element> <i ustaw `mode` atrybut na `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="cf008-165">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4. <span data-ttu-id="cf008-166">Dodaj `transport` element> <i ustaw `clientCredentialType` atrybut na `Windows` .</span><span class="sxs-lookup"><span data-stu-id="cf008-166">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5. <span data-ttu-id="cf008-167">Dodaj `message` element> <i ustaw `clientCredentialType` odpowiednią wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cf008-167">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="cf008-168">Poniższy kod ustawia wartość dla certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="cf008-168">The following code sets the value to a certificate.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf008-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf008-169">See also</span></span>

- [<span data-ttu-id="cf008-170">Instrukcje: ustawianie trybu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="cf008-170">How to: Set the Security Mode</span></span>](../how-to-set-the-security-mode.md)
- [<span data-ttu-id="cf008-171">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="cf008-171">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="cf008-172">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="cf008-172">Securing Services and Clients</span></span>](securing-services-and-clients.md)
