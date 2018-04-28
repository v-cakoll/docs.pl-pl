---
title: 'Instrukcje: Korzystanie z zabezpieczeń transportu i poświadczeń komunikatów'
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
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
caps.latest.revision: 11
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: fad7970711435cdabecd883f5e1dc44c64bd2c93
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="248fe-102">Instrukcje: Korzystanie z zabezpieczeń transportu i poświadczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="248fe-102">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="248fe-103">Zabezpieczanie usługi za pomocą poświadczeń transportowe i komunikatów używa najlepiej tryby zabezpieczenia transportowe i komunikatów w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="248fe-103">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="248fe-104">W sum transport layer security zapewnia integralności i poufności, gdy komunikat warstwy zabezpieczeń zawiera szereg poświadczenia, które nie są możliwe za pomocą mechanizmów zabezpieczeń transportu strict.</span><span class="sxs-lookup"><span data-stu-id="248fe-104">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="248fe-105">W tym temacie przedstawiono podstawowe czynności w przypadku implementowania transportu z poświadczeniami komunikatu za pomocą <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.NetTcpBinding> powiązania.</span><span class="sxs-lookup"><span data-stu-id="248fe-105">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="248fe-106"> Ustawianie trybu zabezpieczeń, zobacz [porady: Ustawianie trybu zabezpieczeń](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="248fe-106"> setting the security mode, see [How to: Set the Security Mode](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="248fe-107">Podczas ustawiania trybu zabezpieczeń `TransportWithMessageCredential`, transport określa konkretny mechanizm, który zapewnia zabezpieczeń na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="248fe-107">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="248fe-108">W przypadku protokołu HTTP mechanizm jest Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP (HTTPS); TCP jest protokół SSL za pośrednictwem protokołu TCP lub systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="248fe-108">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="248fe-109">W przypadku transportu HTTP (przy użyciu <xref:System.ServiceModel.WSHttpBinding>), SSL za pośrednictwem protokołu HTTP zapewnia zabezpieczeń na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="248fe-109">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="248fe-110">W takim przypadku należy skonfigurować komputer obsługujący usługę za pomocą certyfikatu SSL powiązany z portem, jak pokazano w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="248fe-110">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="248fe-111">W przypadku transportu TCP (przy użyciu <xref:System.ServiceModel.NetTcpBinding>), domyślnie zabezpieczeń poziomu transportu jest zabezpieczenia systemu Windows lub SSL za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="248fe-111">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="248fe-112">Przy użyciu protokołu SSL za pośrednictwem protokołu TCP, należy określić certyfikat przy użyciu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody, jak pokazano w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="248fe-112">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="248fe-113">Aby użyć klasy WSHttpBinding przy użyciu certyfikatu zabezpieczeń transportu (w kodzie)</span><span class="sxs-lookup"><span data-stu-id="248fe-113">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="248fe-114">Użyj narzędzia HttpCfg.exe można powiązać certyfikatu SSL z portem na maszynie.</span><span class="sxs-lookup"><span data-stu-id="248fe-114">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> <span data-ttu-id="248fe-115">Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="248fe-115">For more information, see [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2.  <span data-ttu-id="248fe-116">Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> właściwości <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="248fe-116">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3.  <span data-ttu-id="248fe-117">Ustaw <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> właściwości odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="248fe-117">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="248fe-118">(Aby uzyskać więcej informacji, zobacz [Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartość.</span><span class="sxs-lookup"><span data-stu-id="248fe-118">(For more information, see [Selecting a Credential Type](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4.  <span data-ttu-id="248fe-119">Utwórz wystąpienie <xref:System.Uri> klasy przy użyciu odpowiedniego adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="248fe-119">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="248fe-120">Należy pamiętać, że adres musi używać schematu "HTTPS" i musi zawierać rzeczywistą nazwą komputera i numer portu, który jest powiązany certyfikat SSL.</span><span class="sxs-lookup"><span data-stu-id="248fe-120">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="248fe-121">(Alternatywnie można ustawić adres podstawowy w konfiguracji.)</span><span class="sxs-lookup"><span data-stu-id="248fe-121">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5.  <span data-ttu-id="248fe-122">Dodawanie punktu końcowego usługi za pomocą <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="248fe-122">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6.  <span data-ttu-id="248fe-123">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> i Wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> metody, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="248fe-123">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="248fe-124">Aby użyć NetTcpBinding z certyfikatem zabezpieczeń transportu (w kodzie)</span><span class="sxs-lookup"><span data-stu-id="248fe-124">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="248fe-125">Utwórz wystąpienie <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> właściwości <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="248fe-125">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2.  <span data-ttu-id="248fe-126">Ustaw <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="248fe-126">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="248fe-127">Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartość.</span><span class="sxs-lookup"><span data-stu-id="248fe-127">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3.  <span data-ttu-id="248fe-128">Utwórz wystąpienie <xref:System.Uri> klasy przy użyciu odpowiedniego adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="248fe-128">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="248fe-129">Należy pamiętać, że adres musi używać schematu "net.tcp".</span><span class="sxs-lookup"><span data-stu-id="248fe-129">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="248fe-130">(Alternatywnie można ustawić adres podstawowy w konfiguracji.)</span><span class="sxs-lookup"><span data-stu-id="248fe-130">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4.  <span data-ttu-id="248fe-131">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy.</span><span class="sxs-lookup"><span data-stu-id="248fe-131">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5.  <span data-ttu-id="248fe-132">Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy jawnie ustaw certyfikatu X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="248fe-132">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6.  <span data-ttu-id="248fe-133">Dodawanie punktu końcowego usługi za pomocą <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="248fe-133">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7.  <span data-ttu-id="248fe-134">Wywołanie <xref:System.ServiceModel.ICommunicationObject.Open%2A> metody, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="248fe-134">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="248fe-135">Aby użyć NetTcpBinding z systemem Windows dla zabezpieczeń transportu (w kodzie)</span><span class="sxs-lookup"><span data-stu-id="248fe-135">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="248fe-136">Utwórz wystąpienie <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> właściwości <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="248fe-136">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2.  <span data-ttu-id="248fe-137">Ustawienia zabezpieczeń transportu do używania systemu Windows przez ustawienie <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> do <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="248fe-137">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="248fe-138">(Należy pamiętać, że jest to wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="248fe-138">(Note that this is the default.)</span></span>  
  
3.  <span data-ttu-id="248fe-139">Ustaw <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="248fe-139">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="248fe-140">Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartość.</span><span class="sxs-lookup"><span data-stu-id="248fe-140">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4.  <span data-ttu-id="248fe-141">Utwórz wystąpienie <xref:System.Uri> klasy przy użyciu odpowiedniego adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="248fe-141">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="248fe-142">Należy pamiętać, że adres musi używać schematu "net.tcp".</span><span class="sxs-lookup"><span data-stu-id="248fe-142">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="248fe-143">(Alternatywnie można ustawić adres podstawowy w konfiguracji.)</span><span class="sxs-lookup"><span data-stu-id="248fe-143">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5.  <span data-ttu-id="248fe-144">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy.</span><span class="sxs-lookup"><span data-stu-id="248fe-144">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6.  <span data-ttu-id="248fe-145">Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy jawnie ustaw certyfikatu X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="248fe-145">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7.  <span data-ttu-id="248fe-146">Dodawanie punktu końcowego usługi za pomocą <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="248fe-146">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8.  <span data-ttu-id="248fe-147">Wywołanie <xref:System.ServiceModel.ICommunicationObject.Open%2A> metody, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="248fe-147">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="248fe-148">Za pomocą konfiguracji</span><span class="sxs-lookup"><span data-stu-id="248fe-148">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="248fe-149">Aby użyć klasy WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="248fe-149">To use the WSHttpBinding</span></span>  
  
1.  <span data-ttu-id="248fe-150">Skonfiguruj komputer z certyfikatem SSL powiązany z portem.</span><span class="sxs-lookup"><span data-stu-id="248fe-150">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="248fe-151">(Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)).</span><span class="sxs-lookup"><span data-stu-id="248fe-151">(For more information, see [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="248fe-152">Nie należy ustawić <`transport`> Wartość elementu z tą konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="248fe-152">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2.  <span data-ttu-id="248fe-153">Określ typ poświadczeń klienta dla zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="248fe-153">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="248fe-154">W poniższym przykładzie `clientCredentialType` atrybut <`message`> elementu `UserName`.</span><span class="sxs-lookup"><span data-stu-id="248fe-154">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="248fe-155">Aby użyć NetTcpBinding z certyfikatem zabezpieczeń transportu</span><span class="sxs-lookup"><span data-stu-id="248fe-155">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1.  <span data-ttu-id="248fe-156">Dla protokołu SSL za pośrednictwem protokołu TCP, należy jawnie określić certyfikat w `<behaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="248fe-156">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="248fe-157">W poniższym przykładzie przez jego wystawcę certyfikatu w domyślnej lokalizacji magazynu (komputer lokalny i magazyny osobiste).</span><span class="sxs-lookup"><span data-stu-id="248fe-157">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
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
  
2.  <span data-ttu-id="248fe-158">Dodaj [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) do sekcji powiązania</span><span class="sxs-lookup"><span data-stu-id="248fe-158">Add a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3.  <span data-ttu-id="248fe-159">Dodaj element powiązania i ustaw `name` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="248fe-159">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4.  <span data-ttu-id="248fe-160">Dodaj <`security`> element i ustaw `mode` atrybutu `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="248fe-160">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5.  <span data-ttu-id="248fe-161">Dodaj <`message>` element i ustaw `clientCredentialType` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="248fe-161">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
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
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="248fe-162">Aby użyć NetTcpBinding z systemem Windows dla zabezpieczeń transportu</span><span class="sxs-lookup"><span data-stu-id="248fe-162">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1.  <span data-ttu-id="248fe-163">Dodaj [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) do sekcji powiązania</span><span class="sxs-lookup"><span data-stu-id="248fe-163">Add a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2.  <span data-ttu-id="248fe-164">Dodaj <`binding`> element i ustaw `name` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="248fe-164">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="248fe-165">Dodaj <`security`> element i ustaw `mode` atrybutu `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="248fe-165">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4.  <span data-ttu-id="248fe-166">Dodaj <`transport`> element i ustaw `clientCredentialType` atrybutu `Windows`.</span><span class="sxs-lookup"><span data-stu-id="248fe-166">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5.  <span data-ttu-id="248fe-167">Dodaj <`message`> element i ustaw `clientCredentialType` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="248fe-167">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="248fe-168">Poniższy kod ustawia wartość do certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="248fe-168">The following code sets the value to a certificate.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="248fe-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="248fe-169">See Also</span></span>  
 [<span data-ttu-id="248fe-170">Instrukcje: ustawianie trybu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="248fe-170">How to: Set the Security Mode</span></span>](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [<span data-ttu-id="248fe-171">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="248fe-171">Securing Services</span></span>](../../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="248fe-172">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="248fe-172">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
