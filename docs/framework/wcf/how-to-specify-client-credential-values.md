---
title: 'Instrukcje: Określanie wartości poświadczeń klienta'
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
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 35244032a36af8d3d23fd9d88006ea032a99b44b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="01b96-102">Instrukcje: Określanie wartości poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="01b96-102">How to: Specify Client Credential Values</span></span>
<span data-ttu-id="01b96-103">Przy użyciu [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], usługi można określić, jak klient jest uwierzytelniony do usługi.</span><span class="sxs-lookup"><span data-stu-id="01b96-103">Using [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="01b96-104">Na przykład usługi można określić uwierzytelnienia klienta przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="01b96-104">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>  
  
### <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="01b96-105">Aby określić typ poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="01b96-105">To determine the client credential type</span></span>  
  
1.  <span data-ttu-id="01b96-106">Pobieranie metadanych z punktu końcowego metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="01b96-106">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="01b96-107">Metadane zazwyczaj składa się z dwóch plików: Kod klienta w języku programowania wybranym (wartość domyślna to Visual C#) i pliku konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="01b96-107">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="01b96-108">Jednym ze sposobów pobierania metadanych jest korzystać z narzędzia Svcutil.exe do zwrócenia kod klienta i konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="01b96-108">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="01b96-109">Aby uzyskać więcej informacji, zobacz [pobierania metadanych](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) i [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="01b96-109">For more information, see [Retrieving Metadata](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
2.  <span data-ttu-id="01b96-110">Otwórz plik konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="01b96-110">Open the XML configuration file.</span></span> <span data-ttu-id="01b96-111">Jeśli korzystasz z narzędzia Svcutil.exe w domyślnej nazwy pliku jest Output.config.</span><span class="sxs-lookup"><span data-stu-id="01b96-111">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>  
  
3.  <span data-ttu-id="01b96-112">Znajdź  **\<zabezpieczeń >** element z **tryb** atrybutu (**< tryb zabezpieczeń =** `MessageOrTransport` **>** gdzie `MessageOrTransport` jest ustawiona na jeden z trybów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="01b96-112">Find the **\<security>** element with the **mode** attribute (**<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>  
  
4.  <span data-ttu-id="01b96-113">Znajdź element podrzędny, która jest zgodna z wartością tryb.</span><span class="sxs-lookup"><span data-stu-id="01b96-113">Find the child element that matches the mode value.</span></span> <span data-ttu-id="01b96-114">Na przykład, jeśli ustawiono tryb **komunikat**, Znajdź  **\<wiadomości >** element zawarty w  **\<zabezpieczeń >** elementu.</span><span class="sxs-lookup"><span data-stu-id="01b96-114">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>  
  
5.  <span data-ttu-id="01b96-115">Zwróć uwagę na wartość przypisana do **clientCredentialType** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="01b96-115">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="01b96-116">Bieżąca wartość zależy od tego, który tryb jest używany, transportu lub wiadomości.</span><span class="sxs-lookup"><span data-stu-id="01b96-116">The actual value depends on which mode is used, transport or message.</span></span>  
  
 <span data-ttu-id="01b96-117">Poniższy kod XML przedstawia konfigurację korzystanie z zabezpieczeń komunikatów i wymaga certyfikatu klienta do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="01b96-117">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="01b96-118">Przykład: Tryb transportu protokołu TCP z certyfikatu jako poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="01b96-118">Example: TCP Transport Mode with Certificate as Client Credential</span></span>  
 <span data-ttu-id="01b96-119">W tym przykładzie ustawiono tryb zabezpieczeń transportu i ustawia wartość poświadczenia klienta certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="01b96-119">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="01b96-120">Poniższe procedury pokazują, jak można ustawić wartości poświadczeń klienta na komputerze klienckim w kodzie i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="01b96-120">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="01b96-121">Przy założeniu, że użyto [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do zwracania metadanych (kod i konfiguracja) z usługi.</span><span class="sxs-lookup"><span data-stu-id="01b96-121">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="01b96-122">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="01b96-122">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="01b96-123">Aby określić wartość poświadczenia klienta na komputerze klienckim w kodzie</span><span class="sxs-lookup"><span data-stu-id="01b96-123">To specify the client credential value on the client in code</span></span>  
  
1.  <span data-ttu-id="01b96-124">Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania kodu i konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="01b96-124">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>  
  
2.  <span data-ttu-id="01b96-125">Utwórz wystąpienie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta przy użyciu wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="01b96-125">Create an instance of the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client using the generated code.</span></span>  
  
3.  <span data-ttu-id="01b96-126">W klasie klienta, należy ustawić <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość <xref:System.ServiceModel.ClientBase%601> klasy odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="01b96-126">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="01b96-127">W tym przykładzie ustawiono właściwość certyfikatu X.509 przy użyciu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> klasy.</span><span class="sxs-lookup"><span data-stu-id="01b96-127">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     <span data-ttu-id="01b96-128">Można użyć dowolnego z wyliczenia o <xref:System.Security.Cryptography.X509Certificates.X509FindType> klasy.</span><span class="sxs-lookup"><span data-stu-id="01b96-128">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="01b96-129">Nazwa podmiotu jest używany w tym miejscu, w przypadku zmiany certyfikatu (ze względu na datę wygaśnięcia).</span><span class="sxs-lookup"><span data-stu-id="01b96-129">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="01b96-130">Za pomocą nazwy podmiotu umożliwia infrastruktury znaleźć certyfikat ponownie.</span><span class="sxs-lookup"><span data-stu-id="01b96-130">Using the subject name enables the infrastructure to find the certificate again.</span></span>  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="01b96-131">Aby określić wartość poświadczenia klienta na komputerze klienckim w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="01b96-131">To specify the client credential value on the client in configuration</span></span>  
  
1.  <span data-ttu-id="01b96-132">Dodaj [ \<zachowanie >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu [ \<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="01b96-132">Add a [\<behavior>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
2.  <span data-ttu-id="01b96-133">Dodaj [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu [ \<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="01b96-133">Add a [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="01b96-134">Należy ustawić wymaganych `name` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="01b96-134">Be sure to set the required `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="01b96-135">Dodaj [ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) elementu [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="01b96-135">Add a [\<clientCertificate>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
4.  <span data-ttu-id="01b96-136">Ustaw następujące atrybuty odpowiednie wartości: `storeLocation`, `storeName`, `x509FindType`, i `findValue`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="01b96-136">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="01b96-137"> certyfikaty, zobacz [Praca z certyfikatami](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="01b96-137"> certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
    ```xml  
    <behaviors>  
       <endpointBehaviors>  
          <behavior name="endpointCredentialBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="Contoso.com"   
                                 storeLocation="LocalMachine"  
                                 storeName="TrustedPeople"  
                                 x509FindType="FindBySubjectName" />  
            </clientCredentials>  
          </behavior>  
       </endpointBehaviors>  
    </behaviors>  
    ```  
  
5.  <span data-ttu-id="01b96-138">Podczas konfigurowania klienta, Określ zachowanie przez ustawienie `behaviorConfiguration` atrybutu `<endpoint>` element, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="01b96-138">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="01b96-139">Element punktu końcowego jest elementem podrzędnym [ \<klienta >](../../../docs/framework/configure-apps/file-schema/wcf/client.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="01b96-139">The endpoint element is a child of the [\<client>](../../../docs/framework/configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="01b96-140">Ponadto określ nazwę konfiguracji powiązania, ustawiając `bindingConfiguration` atrybutu w celu powiązania dla klienta.</span><span class="sxs-lookup"><span data-stu-id="01b96-140">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="01b96-141">Jeśli używasz plik konfiguracji wygenerowane automatycznie generowana jest nazwa wiązania.</span><span class="sxs-lookup"><span data-stu-id="01b96-141">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="01b96-142">W tym przykładzie nazwa jest `"tcpBindingWithCredential"`.</span><span class="sxs-lookup"><span data-stu-id="01b96-142">In this example, the name is `"tcpBindingWithCredential"`.</span></span>  
  
    ```xml  
    <client>  
      <endpoint name =""  
                address="net.tcp://contoso.com:8036/aloha"  
                binding="netTcpBinding"  
                bindingConfiguration="tcpBindingWithCredential"  
                behaviorConfiguration="endpointCredentialBehavior" />  
    </client>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="01b96-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01b96-143">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.ClientBase%601>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>  
 [<span data-ttu-id="01b96-144">Programowanie zabezpieczeń WCF</span><span class="sxs-lookup"><span data-stu-id="01b96-144">Programming WCF Security</span></span>](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [<span data-ttu-id="01b96-145">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="01b96-145">Selecting a Credential Type</span></span>](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="01b96-146">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="01b96-146">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="01b96-147">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="01b96-147">Working with Certificates</span></span>](../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="01b96-148">Instrukcje: tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="01b96-148">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="01b96-149">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="01b96-149">\<netTcpBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)  
 [<span data-ttu-id="01b96-150">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="01b96-150">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
 [<span data-ttu-id="01b96-151">\<message></span><span class="sxs-lookup"><span data-stu-id="01b96-151">\<message></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)  
 [<span data-ttu-id="01b96-152">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="01b96-152">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)  
 [<span data-ttu-id="01b96-153">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="01b96-153">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [<span data-ttu-id="01b96-154">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="01b96-154">\<clientCertificate></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)  
 [<span data-ttu-id="01b96-155">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="01b96-155">\<clientCredentials></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
