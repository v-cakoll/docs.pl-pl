---
title: 'Instrukcje: Zabezpieczanie usługi za pomocą certyfikatu X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 73fd9919d1403ef592e5b81c11b6eb659baea669
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a><span data-ttu-id="7ef83-102">Instrukcje: Zabezpieczanie usługi za pomocą certyfikatu X.509</span><span class="sxs-lookup"><span data-stu-id="7ef83-102">How to: Secure a Service with an X.509 Certificate</span></span>
<span data-ttu-id="7ef83-103">Zabezpieczanie usługi za pomocą certyfikatu X.509 to technika podstawowe, używanego przez większość powiązania w systemie Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7ef83-103">Securing a service with an X.509 certificate is a basic technique that most bindings in Windows Communication Foundation (WCF) use.</span></span> <span data-ttu-id="7ef83-104">W tym temacie przedstawiono kroki konfigurowania samodzielnie hostowana usługa za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="7ef83-104">This topic walks through the steps of configuring a self-hosted service with an X.509 certificate.</span></span>  
  
 <span data-ttu-id="7ef83-105">Warunkiem wstępnym jest ważny certyfikat, który może służyć do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="7ef83-105">A prerequisite is a valid certificate that can be used to authenticate the server.</span></span> <span data-ttu-id="7ef83-106">Certyfikat musi wystawiony na serwerze przez zaufany urząd certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="7ef83-106">The certificate must be issued to the server by a trusted certificate authority.</span></span> <span data-ttu-id="7ef83-107">Jeśli certyfikat nie jest prawidłowy, każdy klient próbuje użyć usługi nie ufa usługi, a w związku z tym połączenie nie zostanie ustanowione.</span><span class="sxs-lookup"><span data-stu-id="7ef83-107">If the certificate is not valid, any client trying to use the service will not trust the service, and consequently no connection will be made.</span></span> <span data-ttu-id="7ef83-108">Aby uzyskać więcej informacji o korzystaniu z certyfikatów, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7ef83-108">For more information about using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a><span data-ttu-id="7ef83-109">Aby skonfigurować usługę przy użyciu certyfikatu przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="7ef83-109">To configure a service with a certificate using code</span></span>  
  
1.  <span data-ttu-id="7ef83-110">Utworzyć kontrakt usługi i Usługa zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="7ef83-110">Create the service contract and the implemented service.</span></span> <span data-ttu-id="7ef83-111">Aby uzyskać więcej informacji, zobacz [projektowanie i Implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="7ef83-111">For more information, see [Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md).</span></span>  
  
2.  <span data-ttu-id="7ef83-112">Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń <xref:System.ServiceModel.SecurityMode.Message>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="7ef83-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3.  <span data-ttu-id="7ef83-113">Utwórz dwa <xref:System.Type> zmiennych, z których jeden typ kontraktu i zaimplementowanego kontraktu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="7ef83-113">Create two <xref:System.Type> variables, one each for the contract type and the implemented contract, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4.  <span data-ttu-id="7ef83-114">Utwórz wystąpienie <xref:System.Uri> klasy dla podstawowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="7ef83-114">Create an instance of the <xref:System.Uri> class for the base address of the service.</span></span> <span data-ttu-id="7ef83-115">Ponieważ `WSHttpBinding` używa transportu HTTP, jednolity identyfikator zasobów (URI) musi zaczynać się od tego schematu lub Windows Communication Foundation (WCF) spowoduje zgłoszenie wyjątku, gdy usługa jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="7ef83-115">Because the `WSHttpBinding` uses the HTTP transport, the Uniform Resource Identifier (URI) must begin with that schema, or Windows Communication Foundation (WCF) will throw an exception when the service is opened.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5.  <span data-ttu-id="7ef83-116">Utwórz nowe wystąpienie klasy <xref:System.ServiceModel.ServiceHost> klasy z zaimplementowanym kontrakcie typu zmienną i identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="7ef83-116">Create a new instance of the <xref:System.ServiceModel.ServiceHost> class with the implemented contract type variable and the URI.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6.  <span data-ttu-id="7ef83-117">Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> do usługi przy użyciu <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7ef83-117">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> to the service using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span> <span data-ttu-id="7ef83-118">Przekaż kontraktu, powiązania i adresu punktu końcowego dla konstruktora, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="7ef83-118">Pass the contract, binding, and an endpoint address to the constructor, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7.  <span data-ttu-id="7ef83-119">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7ef83-119">Optional.</span></span> <span data-ttu-id="7ef83-120">Aby pobrać metadane z usługi, Utwórz nową <xref:System.ServiceModel.Description.ServiceMetadataBehavior> obiektu i ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="7ef83-120">To retrieve metadata from the service, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> object and set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8.  <span data-ttu-id="7ef83-121">Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasę, aby dodać prawidłowy certyfikat do usługi.</span><span class="sxs-lookup"><span data-stu-id="7ef83-121">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to add the valid certificate to the service.</span></span> <span data-ttu-id="7ef83-122">Metoda może używać jednej z kilku metod można znaleźć certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="7ef83-122">The method can use one of several methods to find a certificate.</span></span> <span data-ttu-id="7ef83-123">W tym przykładzie użyto <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7ef83-123">This example uses the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> enumeration.</span></span> <span data-ttu-id="7ef83-124">Wyliczenie Określa, czy podana wartość jest nazwą jednostki, który certyfikat został wystawiony dla.</span><span class="sxs-lookup"><span data-stu-id="7ef83-124">The enumeration specifies that the supplied value is the name of the entity that the certificate was issued to.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. <span data-ttu-id="7ef83-125">Wywołanie <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metodę, aby rozpocząć nasłuchiwania usługi.</span><span class="sxs-lookup"><span data-stu-id="7ef83-125">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service listening.</span></span> <span data-ttu-id="7ef83-126">W przypadku tworzenia aplikacji konsoli, należy wywołać <xref:System.Console.ReadLine%2A> metody, aby zapewnić usługę w stanie nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="7ef83-126">If you are creating a console application, call the <xref:System.Console.ReadLine%2A> method to keep the service in the listening state.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="7ef83-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="7ef83-127">Example</span></span>  
 <span data-ttu-id="7ef83-128">W poniższym przykładzie użyto <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodę, aby skonfigurować usługę za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="7ef83-128">The following example uses the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method to configure a service with an X.509 certificate.</span></span>  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7ef83-129">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7ef83-129">Compiling the Code</span></span>  
 <span data-ttu-id="7ef83-130">Następujących przestrzeni nazw są wymagane, aby skompilować kod:</span><span class="sxs-lookup"><span data-stu-id="7ef83-130">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.Web.Services.Description>  
  
-   <xref:System.Security.Cryptography.X509Certificates>  
  
-   <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a><span data-ttu-id="7ef83-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ef83-131">See Also</span></span>  
 [<span data-ttu-id="7ef83-132">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="7ef83-132">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
