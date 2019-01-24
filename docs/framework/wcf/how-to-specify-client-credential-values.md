---
title: 'Instrukcje: Określanie wartości poświadczeń klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 110b8ffe2fb3e00d7a6787e32d066f62126ebf9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617190"
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="9bc97-102">Instrukcje: Określanie wartości poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="9bc97-102">How to: Specify Client Credential Values</span></span>
<span data-ttu-id="9bc97-103">Za pomocą usługi Windows Communication Foundation (WCF), usługi można określić, jak klient jest uwierzytelniany w usłudze.</span><span class="sxs-lookup"><span data-stu-id="9bc97-103">Using Windows Communication Foundation (WCF), the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="9bc97-104">Na przykład usługi można zastrzec uwierzytelnienia klienta przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="9bc97-104">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>  
  
### <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="9bc97-105">Aby określić typ poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="9bc97-105">To determine the client credential type</span></span>  
  
1.  <span data-ttu-id="9bc97-106">Pobieranie metadanych z punktu końcowego metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="9bc97-106">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="9bc97-107">Metadane zazwyczaj składa się z dwóch plików: Kod klienta w wybranym języku programowania (wartość domyślna to Visual C#), a plik konfiguracyjny XML.</span><span class="sxs-lookup"><span data-stu-id="9bc97-107">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="9bc97-108">Jest jednym ze sposobów, aby pobrać metadane na potrzeby narzędzia Svcutil.exe zwrócić kod klienta i konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="9bc97-108">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="9bc97-109">Aby uzyskać więcej informacji, zobacz [podczas pobierania metadanych](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) i [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9bc97-109">For more information, see [Retrieving Metadata](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
2.  <span data-ttu-id="9bc97-110">Otwórz plik konfiguracyjny XML.</span><span class="sxs-lookup"><span data-stu-id="9bc97-110">Open the XML configuration file.</span></span> <span data-ttu-id="9bc97-111">Jeśli używasz narzędzia Svcutil.exe, domyślna nazwa pliku jest Output.config.</span><span class="sxs-lookup"><span data-stu-id="9bc97-111">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>  
  
3.  <span data-ttu-id="9bc97-112">Znajdź  **\<zabezpieczeń >** element z **tryb** atrybutu (**< tryb zabezpieczeń =** `MessageOrTransport` **>** gdzie `MessageOrTransport` jest ustawiona na jeden z trybów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9bc97-112">Find the **\<security>** element with the **mode** attribute (**<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>  
  
4.  <span data-ttu-id="9bc97-113">Znajdź element podrzędny, który odpowiada wartość trybu.</span><span class="sxs-lookup"><span data-stu-id="9bc97-113">Find the child element that matches the mode value.</span></span> <span data-ttu-id="9bc97-114">Na przykład, jeśli jest tryb **komunikat**, Znajdź  **\<komunikatu >** elementów znajdujących się w  **\<zabezpieczeń >** elementu.</span><span class="sxs-lookup"><span data-stu-id="9bc97-114">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>  
  
5.  <span data-ttu-id="9bc97-115">Zwróć uwagę na wartość przypisana do **clientCredentialType** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9bc97-115">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="9bc97-116">Wartość rzeczywista zależy od tego, który tryb jest używany, transportu lub komunikatu.</span><span class="sxs-lookup"><span data-stu-id="9bc97-116">The actual value depends on which mode is used, transport or message.</span></span>  
  
 <span data-ttu-id="9bc97-117">Następujący kod XML przedstawia konfigurację dla korzystanie z zabezpieczeń komunikatów co wymaga certyfikatu klienta do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="9bc97-117">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="9bc97-118">Przykład: Tryb transportu TCP za pomocą certyfikatu jako poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="9bc97-118">Example: TCP Transport Mode with Certificate as Client Credential</span></span>  
 <span data-ttu-id="9bc97-119">W tym przykładzie Ustawia tryb zabezpieczeń transportu i ustawia wartość poświadczenia klienta certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="9bc97-119">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="9bc97-120">Poniższe procedury pokazują, jak można ustawić wartości poświadczeń klienta na komputerze klienckim w kodzie i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9bc97-120">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="9bc97-121">Założono, że korzystasz z [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) zwrócić metadanych (kod i konfiguracji) z usługi.</span><span class="sxs-lookup"><span data-stu-id="9bc97-121">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="9bc97-122">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="9bc97-122">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="9bc97-123">Aby określić wartości poświadczeń klienta na komputerze klienckim w kodzie</span><span class="sxs-lookup"><span data-stu-id="9bc97-123">To specify the client credential value on the client in code</span></span>  
  
1.  <span data-ttu-id="9bc97-124">Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania kodu i konfiguracji z usługi.</span><span class="sxs-lookup"><span data-stu-id="9bc97-124">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>  
  
2.  <span data-ttu-id="9bc97-125">Utwórz wystąpienie klienta WCF, za pomocą wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="9bc97-125">Create an instance of the WCF client using the generated code.</span></span>  
  
3.  <span data-ttu-id="9bc97-126">W klasie klienta ustaw <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość <xref:System.ServiceModel.ClientBase%601> klasy do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="9bc97-126">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="9bc97-127">W tym przykładzie ustawia właściwość do certyfikatów X.509 przy użyciu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> klasy.</span><span class="sxs-lookup"><span data-stu-id="9bc97-127">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     <span data-ttu-id="9bc97-128">Można użyć dowolnego z wyliczenia o <xref:System.Security.Cryptography.X509Certificates.X509FindType> klasy.</span><span class="sxs-lookup"><span data-stu-id="9bc97-128">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="9bc97-129">Nazwa podmiotu jest używany w tym miejscu, w przypadku, gdy certyfikat jest zmieniony (ze względu na datę wygaśnięcia).</span><span class="sxs-lookup"><span data-stu-id="9bc97-129">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="9bc97-130">Przy użyciu nazwy podmiotu umożliwia infrastruktury można znaleźć certyfikatu ponownie.</span><span class="sxs-lookup"><span data-stu-id="9bc97-130">Using the subject name enables the infrastructure to find the certificate again.</span></span>  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="9bc97-131">Aby określić wartości poświadczeń klienta na komputerze klienckim w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9bc97-131">To specify the client credential value on the client in configuration</span></span>  
  
1.  <span data-ttu-id="9bc97-132">Dodaj [ \<zachowanie >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu [ \<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="9bc97-132">Add a [\<behavior>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
2.  <span data-ttu-id="9bc97-133">Dodaj [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu [ \<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="9bc97-133">Add a [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="9bc97-134">Pamiętaj ustawić wymaganych `name` atrybutu do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="9bc97-134">Be sure to set the required `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="9bc97-135">Dodaj [ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) elementu [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="9bc97-135">Add a [\<clientCertificate>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
4.  <span data-ttu-id="9bc97-136">Ustaw następujące atrybuty odpowiednie wartości: `storeLocation`, `storeName`, `x509FindType`, i `findValue`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9bc97-136">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="9bc97-137">Aby uzyskać więcej informacji na temat certyfikatów, zobacz [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="9bc97-137">For more information about certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
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
  
5.  <span data-ttu-id="9bc97-138">Podczas konfigurowania klienta należy określić zachowanie przez ustawienie `behaviorConfiguration` atrybutu `<endpoint>` elementu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9bc97-138">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="9bc97-139">Punkt końcowy element jest elementem podrzędnym [ \<klienta >](../../../docs/framework/configure-apps/file-schema/wcf/client.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="9bc97-139">The endpoint element is a child of the [\<client>](../../../docs/framework/configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="9bc97-140">Ponadto należy określić nazwę konfiguracji powiązania, ustawiając `bindingConfiguration` atrybut do powiązania dla klienta.</span><span class="sxs-lookup"><span data-stu-id="9bc97-140">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="9bc97-141">Jeśli używasz pliku konfiguracji wygenerowanego Nazwa powiązania jest generowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="9bc97-141">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="9bc97-142">W tym przykładzie nazwa to `"tcpBindingWithCredential"`.</span><span class="sxs-lookup"><span data-stu-id="9bc97-142">In this example, the name is `"tcpBindingWithCredential"`.</span></span>  
  
    ```xml  
    <client>  
      <endpoint name =""  
                address="net.tcp://contoso.com:8036/aloha"  
                binding="netTcpBinding"  
                bindingConfiguration="tcpBindingWithCredential"  
                behaviorConfiguration="endpointCredentialBehavior" />  
    </client>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9bc97-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9bc97-143">See also</span></span>
- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="9bc97-144">Programowanie zabezpieczeń WCF</span><span class="sxs-lookup"><span data-stu-id="9bc97-144">Programming WCF Security</span></span>](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [<span data-ttu-id="9bc97-145">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="9bc97-145">Selecting a Credential Type</span></span>](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="9bc97-146">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="9bc97-146">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="9bc97-147">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="9bc97-147">Working with Certificates</span></span>](../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="9bc97-148">Instrukcje: Tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="9bc97-148">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="9bc97-149">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="9bc97-149">\<netTcpBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)
- [<span data-ttu-id="9bc97-150">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="9bc97-150">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [<span data-ttu-id="9bc97-151">\<message></span><span class="sxs-lookup"><span data-stu-id="9bc97-151">\<message></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [<span data-ttu-id="9bc97-152">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="9bc97-152">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [<span data-ttu-id="9bc97-153">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="9bc97-153">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [<span data-ttu-id="9bc97-154">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="9bc97-154">\<clientCertificate></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [<span data-ttu-id="9bc97-155">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="9bc97-155">\<clientCredentials></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
