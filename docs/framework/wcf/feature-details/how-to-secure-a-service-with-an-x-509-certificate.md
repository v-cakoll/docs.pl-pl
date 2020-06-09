---
title: 'Instrukcje: Zabezpieczanie usługi za pomocą certyfikatu X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
ms.openlocfilehash: 10d6db63368ee55040f85f922b9483982e8ff264
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596971"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a><span data-ttu-id="f7b89-102">Instrukcje: Zabezpieczanie usługi za pomocą certyfikatu X.509</span><span class="sxs-lookup"><span data-stu-id="f7b89-102">How to: Secure a Service with an X.509 Certificate</span></span>
<span data-ttu-id="f7b89-103">Zabezpieczanie usługi za pomocą certyfikatu X. 509 jest podstawową techniką, która jest używana w większości powiązań w Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f7b89-103">Securing a service with an X.509 certificate is a basic technique that most bindings in Windows Communication Foundation (WCF) use.</span></span> <span data-ttu-id="f7b89-104">W tym temacie przedstawiono kroki konfigurowania usługi samodzielnej przy użyciu certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="f7b89-104">This topic walks through the steps of configuring a self-hosted service with an X.509 certificate.</span></span>  
  
 <span data-ttu-id="f7b89-105">Warunek wstępny jest prawidłowym certyfikatem, którego można użyć do uwierzytelnienia serwera.</span><span class="sxs-lookup"><span data-stu-id="f7b89-105">A prerequisite is a valid certificate that can be used to authenticate the server.</span></span> <span data-ttu-id="f7b89-106">Certyfikat musi zostać wystawiony dla serwera przez zaufany urząd certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="f7b89-106">The certificate must be issued to the server by a trusted certificate authority.</span></span> <span data-ttu-id="f7b89-107">Jeśli certyfikat jest nieprawidłowy, każdy klient próbujący skorzystać z usługi nie będzie ufać usłudze i w związku z tym nie zostanie nawiązane żadne połączenie.</span><span class="sxs-lookup"><span data-stu-id="f7b89-107">If the certificate is not valid, any client trying to use the service will not trust the service, and consequently no connection will be made.</span></span> <span data-ttu-id="f7b89-108">Aby uzyskać więcej informacji o korzystaniu z certyfikatów, zobacz [Praca z certyfikatami](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="f7b89-108">For more information about using certificates, see [Working with Certificates](working-with-certificates.md).</span></span>  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a><span data-ttu-id="f7b89-109">Aby skonfigurować usługę z certyfikatem przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="f7b89-109">To configure a service with a certificate using code</span></span>  
  
1. <span data-ttu-id="f7b89-110">Utwórz kontrakt usługi i zaimplementowaną usługę.</span><span class="sxs-lookup"><span data-stu-id="f7b89-110">Create the service contract and the implemented service.</span></span> <span data-ttu-id="f7b89-111">Aby uzyskać więcej informacji, zobacz [projektowanie i implementowanie usług](../designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="f7b89-111">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md).</span></span>  
  
2. <span data-ttu-id="f7b89-112">Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń na <xref:System.ServiceModel.SecurityMode.Message> , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f7b89-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3. <span data-ttu-id="f7b89-113">Utwórz dwie <xref:System.Type> zmienne, jeden dla typu kontraktu i zaimplementowany kontrakt, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f7b89-113">Create two <xref:System.Type> variables, one each for the contract type and the implemented contract, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4. <span data-ttu-id="f7b89-114">Utwórz wystąpienie <xref:System.Uri> klasy dla adresu podstawowego usługi.</span><span class="sxs-lookup"><span data-stu-id="f7b89-114">Create an instance of the <xref:System.Uri> class for the base address of the service.</span></span> <span data-ttu-id="f7b89-115">Ponieważ `WSHttpBinding` korzysta z transportu HTTP, Uniform Resource Identifier (URI) musi rozpoczynać się od tego schematu lub Windows Communication Foundation (WCF) zgłosi wyjątek, gdy usługa zostanie otwarta.</span><span class="sxs-lookup"><span data-stu-id="f7b89-115">Because the `WSHttpBinding` uses the HTTP transport, the Uniform Resource Identifier (URI) must begin with that schema, or Windows Communication Foundation (WCF) will throw an exception when the service is opened.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5. <span data-ttu-id="f7b89-116">Utwórz nowe wystąpienie <xref:System.ServiceModel.ServiceHost> klasy z zaimplementowaną zmienną typu kontraktu i identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="f7b89-116">Create a new instance of the <xref:System.ServiceModel.ServiceHost> class with the implemented contract type variable and the URI.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6. <span data-ttu-id="f7b89-117">Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> do usługi za pomocą <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f7b89-117">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> to the service using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span> <span data-ttu-id="f7b89-118">Przekaż kontrakt, powiązanie i adres punktu końcowego do konstruktora, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f7b89-118">Pass the contract, binding, and an endpoint address to the constructor, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7. <span data-ttu-id="f7b89-119">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f7b89-119">Optional.</span></span> <span data-ttu-id="f7b89-120">Aby pobrać metadane z usługi, należy utworzyć nowy <xref:System.ServiceModel.Description.ServiceMetadataBehavior> obiekt i ustawić <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> Właściwość na `true` .</span><span class="sxs-lookup"><span data-stu-id="f7b89-120">To retrieve metadata from the service, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> object and set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8. <span data-ttu-id="f7b89-121">Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy, aby dodać prawidłowy certyfikat do usługi.</span><span class="sxs-lookup"><span data-stu-id="f7b89-121">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to add the valid certificate to the service.</span></span> <span data-ttu-id="f7b89-122">Metoda może korzystać z jednej z kilku metod w celu znalezienia certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="f7b89-122">The method can use one of several methods to find a certificate.</span></span> <span data-ttu-id="f7b89-123">W tym przykładzie zastosowano <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="f7b89-123">This example uses the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> enumeration.</span></span> <span data-ttu-id="f7b89-124">Wyliczenie określa, że podana wartość jest nazwą jednostki, w której został wystawiony certyfikat.</span><span class="sxs-lookup"><span data-stu-id="f7b89-124">The enumeration specifies that the supplied value is the name of the entity that the certificate was issued to.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. <span data-ttu-id="f7b89-125">Wywołaj <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metodę, aby rozpocząć nasłuchiwanie usługi.</span><span class="sxs-lookup"><span data-stu-id="f7b89-125">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service listening.</span></span> <span data-ttu-id="f7b89-126">Jeśli tworzysz aplikację konsolową, wywołaj metodę, <xref:System.Console.ReadLine%2A> Aby zachować stan nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="f7b89-126">If you are creating a console application, call the <xref:System.Console.ReadLine%2A> method to keep the service in the listening state.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="f7b89-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7b89-127">Example</span></span>  
 <span data-ttu-id="f7b89-128">W poniższym przykładzie zastosowano <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodę w celu skonfigurowania usługi przy użyciu certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="f7b89-128">The following example uses the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method to configure a service with an X.509 certificate.</span></span>  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f7b89-129">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f7b89-129">Compiling the Code</span></span>  
 <span data-ttu-id="f7b89-130">Do skompilowania kodu wymagane są następujące przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="f7b89-130">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.Web.Services.Description>  
  
- <xref:System.Security.Cryptography.X509Certificates>  
  
- <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a><span data-ttu-id="f7b89-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7b89-131">See also</span></span>

- [<span data-ttu-id="f7b89-132">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="f7b89-132">Working with Certificates</span></span>](working-with-certificates.md)
