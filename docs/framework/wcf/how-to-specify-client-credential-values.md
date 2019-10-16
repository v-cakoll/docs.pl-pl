---
title: 'Instrukcje: Określanie wartości poświadczeń klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 2417c2dd16224d6cbf00d3f1f4a8958420830b6c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319862"
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="cd729-102">Instrukcje: Określanie wartości poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="cd729-102">How to: Specify Client Credential Values</span></span>

<span data-ttu-id="cd729-103">Za pomocą Windows Communication Foundation (WCF) usługa może określić, jak klient jest uwierzytelniany w usłudze.</span><span class="sxs-lookup"><span data-stu-id="cd729-103">Using Windows Communication Foundation (WCF), the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="cd729-104">Na przykład usługa może ustalić, że klient zostanie uwierzytelniony przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="cd729-104">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>

## <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="cd729-105">Aby określić typ poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="cd729-105">To determine the client credential type</span></span>

1. <span data-ttu-id="cd729-106">Pobierz metadane z punktu końcowego metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="cd729-106">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="cd729-107">Metadane zwykle składają się z dwóch plików: kodu klienta w wybranym języku programowania (domyślnie wizualizacji C#) i pliku konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="cd729-107">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="cd729-108">Jednym ze sposobów pobierania metadanych jest użycie narzędzia Svcutil. exe w celu zwrócenia kodu klienta i konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="cd729-108">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="cd729-109">Aby uzyskać więcej informacji, zobacz [Pobieranie metadanych](./feature-details/retrieving-metadata.md) i [Narzędzia ServiceModel metadanych programu (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cd729-109">For more information, see [Retrieving Metadata](./feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

2. <span data-ttu-id="cd729-110">Otwórz plik konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="cd729-110">Open the XML configuration file.</span></span> <span data-ttu-id="cd729-111">Jeśli używasz narzędzia Svcutil. exe, domyślną nazwą pliku jest Output. config.</span><span class="sxs-lookup"><span data-stu-id="cd729-111">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>

3. <span data-ttu-id="cd729-112">Znajdź element **\<security >** z atrybutem **mode** ( **\<security mode =** `MessageOrTransport` **>** , gdzie `MessageOrTransport` jest ustawiony jeden z trybów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="cd729-112">Find the **\<security>** element with the **mode** attribute (**\<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>

4. <span data-ttu-id="cd729-113">Znajdź element podrzędny, który jest zgodny z wartością trybu.</span><span class="sxs-lookup"><span data-stu-id="cd729-113">Find the child element that matches the mode value.</span></span> <span data-ttu-id="cd729-114">Na przykład, jeśli tryb jest ustawiony na wartość **Message**, znajdź element **\<message >** zawarty w elemencie **> \<security** .</span><span class="sxs-lookup"><span data-stu-id="cd729-114">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>

5. <span data-ttu-id="cd729-115">Zwróć uwagę na wartość przypisaną do atrybutu **ClientCredentialType** .</span><span class="sxs-lookup"><span data-stu-id="cd729-115">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="cd729-116">Rzeczywista wartość zależy od tego, który tryb jest używany, transport lub wiadomość.</span><span class="sxs-lookup"><span data-stu-id="cd729-116">The actual value depends on which mode is used, transport or message.</span></span>

<span data-ttu-id="cd729-117">Poniższy kod XML przedstawia konfigurację klienta przy użyciu zabezpieczeń komunikatów i wymaga certyfikatu do uwierzytelnienia klienta.</span><span class="sxs-lookup"><span data-stu-id="cd729-117">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="cd729-118">Przykład: Tryb transportu TCP z certyfikatem jako poświadczenia klienta</span><span class="sxs-lookup"><span data-stu-id="cd729-118">Example: TCP Transport Mode with Certificate as Client Credential</span></span>

<span data-ttu-id="cd729-119">Ten przykład ustawia tryb zabezpieczeń na transport i ustawia wartość poświadczeń klienta na certyfikat X. 509.</span><span class="sxs-lookup"><span data-stu-id="cd729-119">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="cd729-120">W poniższych procedurach pokazano, jak ustawić wartość poświadczenia klienta na kliencie w kodzie i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cd729-120">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="cd729-121">Przyjęto założenie, że użyto [Narzędzia do obsługi metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) w celu zwrócenia metadanych (kodu i konfiguracji) z usługi.</span><span class="sxs-lookup"><span data-stu-id="cd729-121">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="cd729-122">Aby uzyskać więcej informacji, zobacz [How to: Create a Client](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="cd729-122">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="cd729-123">Aby określić wartość poświadczeń klienta w kodzie</span><span class="sxs-lookup"><span data-stu-id="cd729-123">To specify the client credential value on the client in code</span></span>

1. <span data-ttu-id="cd729-124">Użyj narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , aby wygenerować kod i konfigurację z usługi.</span><span class="sxs-lookup"><span data-stu-id="cd729-124">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>

2. <span data-ttu-id="cd729-125">Utwórz wystąpienie klienta WCF przy użyciu wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="cd729-125">Create an instance of the WCF client using the generated code.</span></span>

3. <span data-ttu-id="cd729-126">W klasie Client ustaw właściwość <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> klasy <xref:System.ServiceModel.ClientBase%601> na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="cd729-126">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="cd729-127">Ten przykład ustawia właściwość na certyfikat X. 509 przy użyciu metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> klasy <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.</span><span class="sxs-lookup"><span data-stu-id="cd729-127">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     <span data-ttu-id="cd729-128">Można użyć dowolnego wyliczenia klasy <xref:System.Security.Cryptography.X509Certificates.X509FindType>.</span><span class="sxs-lookup"><span data-stu-id="cd729-128">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="cd729-129">Nazwa podmiotu jest używana w tym miejscu w przypadku zmiany certyfikatu (z powodu daty wygaśnięcia).</span><span class="sxs-lookup"><span data-stu-id="cd729-129">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="cd729-130">Użycie nazwy podmiotu umożliwia ponowne znalezienie certyfikatu przez infrastrukturę.</span><span class="sxs-lookup"><span data-stu-id="cd729-130">Using the subject name enables the infrastructure to find the certificate again.</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="cd729-131">Aby określić wartość poświadczenia klienta w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cd729-131">To specify the client credential value on the client in configuration</span></span>

1. <span data-ttu-id="cd729-132">Dodaj element [\<behavior >](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) do elementu [> \<behaviors](../configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="cd729-132">Add a [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

2. <span data-ttu-id="cd729-133">Dodaj element [\<clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md) do elementu [> \<behaviors](../configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="cd729-133">Add a [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="cd729-134">Upewnij się, że atrybut Required `name` został ustawiony na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="cd729-134">Be sure to set the required `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="cd729-135">Dodaj element [\<clientCertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) do elementu [> \<clientCredentials](../configure-apps/file-schema/wcf/clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="cd729-135">Add a [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>

4. <span data-ttu-id="cd729-136">Ustaw następujące atrybuty na odpowiednie wartości: `storeLocation`, `storeName`, `x509FindType` i `findValue`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="cd729-136">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="cd729-137">Aby uzyskać więcej informacji o certyfikatach, zobacz [Praca z certyfikatami](./feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="cd729-137">For more information about certificates, see [Working with Certificates](./feature-details/working-with-certificates.md).</span></span>

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

5. <span data-ttu-id="cd729-138">Podczas konfigurowania klienta określ zachowanie, ustawiając atrybut `behaviorConfiguration` elementu `<endpoint>`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="cd729-138">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="cd729-139">Element Endpoint jest elementem podrzędnym elementu [\<client >](../configure-apps/file-schema/wcf/client.md) .</span><span class="sxs-lookup"><span data-stu-id="cd729-139">The endpoint element is a child of the [\<client>](../configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="cd729-140">Ponadto Określ nazwę konfiguracji powiązania, ustawiając atrybut `bindingConfiguration` na powiązanie dla klienta.</span><span class="sxs-lookup"><span data-stu-id="cd729-140">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="cd729-141">Jeśli używasz wygenerowanego pliku konfiguracji, nazwa powiązania jest generowana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="cd729-141">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="cd729-142">W tym przykładzie nazwa jest `"tcpBindingWithCredential"`.</span><span class="sxs-lookup"><span data-stu-id="cd729-142">In this example, the name is `"tcpBindingWithCredential"`.</span></span>

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a><span data-ttu-id="cd729-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd729-143">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="cd729-144">Programowanie zabezpieczeń WCF</span><span class="sxs-lookup"><span data-stu-id="cd729-144">Programming WCF Security</span></span>](./feature-details/programming-wcf-security.md)
- [<span data-ttu-id="cd729-145">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="cd729-145">Selecting a Credential Type</span></span>](./feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="cd729-146">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="cd729-146">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="cd729-147">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="cd729-147">Working with Certificates</span></span>](./feature-details/working-with-certificates.md)
- [<span data-ttu-id="cd729-148">Instrukcje: tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="cd729-148">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="cd729-149">@no__t — 1netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="cd729-149">\<netTcpBinding></span></span>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [<span data-ttu-id="cd729-150">@no__t — 1security ></span><span class="sxs-lookup"><span data-stu-id="cd729-150">\<security></span></span>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [<span data-ttu-id="cd729-151">@no__t — 1message ></span><span class="sxs-lookup"><span data-stu-id="cd729-151">\<message></span></span>](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [<span data-ttu-id="cd729-152">@no__t — 1behavior ></span><span class="sxs-lookup"><span data-stu-id="cd729-152">\<behavior></span></span>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [<span data-ttu-id="cd729-153">@no__t — 1behaviors ></span><span class="sxs-lookup"><span data-stu-id="cd729-153">\<behaviors></span></span>](../configure-apps/file-schema/wcf/behaviors.md)
- [<span data-ttu-id="cd729-154">@no__t — 1clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="cd729-154">\<clientCertificate></span></span>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [<span data-ttu-id="cd729-155">@no__t — 1clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="cd729-155">\<clientCredentials></span></span>](../configure-apps/file-schema/wcf/clientcredentials.md)
