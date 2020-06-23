---
title: 'Instrukcje: Określanie wartości poświadczeń klienta'
description: Dowiedz się, w jaki sposób usługa WCF może określić sposób uwierzytelniania klienta w ramach tej usługi. W tym przykładzie określono certyfikat X. 509 i Tryb transportu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 75a21a7dc083282f6b2fe839167ff1b2eddfb373
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244455"
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="0d374-104">Instrukcje: Określanie wartości poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="0d374-104">How to: Specify Client Credential Values</span></span>

<span data-ttu-id="0d374-105">Za pomocą Windows Communication Foundation (WCF) usługa może określić, jak klient jest uwierzytelniany w usłudze.</span><span class="sxs-lookup"><span data-stu-id="0d374-105">Using Windows Communication Foundation (WCF), the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="0d374-106">Na przykład usługa może ustalić, że klient zostanie uwierzytelniony przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="0d374-106">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>

## <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="0d374-107">Aby określić typ poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="0d374-107">To determine the client credential type</span></span>

1. <span data-ttu-id="0d374-108">Pobierz metadane z punktu końcowego metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="0d374-108">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="0d374-109">Metadane zwykle składają się z dwóch plików: kodu klienta w wybranym języku programowania (Domyślnie Visual C#) i pliku konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="0d374-109">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="0d374-110">Jednym ze sposobów pobierania metadanych jest użycie narzędzia Svcutil.exe do zwrócenia kodu klienta i konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="0d374-110">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="0d374-111">Aby uzyskać więcej informacji, zobacz [Pobieranie metadanych](./feature-details/retrieving-metadata.md) i [Narzędzia ServiceModel metadanych (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0d374-111">For more information, see [Retrieving Metadata](./feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

2. <span data-ttu-id="0d374-112">Otwórz plik konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="0d374-112">Open the XML configuration file.</span></span> <span data-ttu-id="0d374-113">Jeśli używasz narzędzia Svcutil.exe, domyślna nazwa pliku jest Output.config.</span><span class="sxs-lookup"><span data-stu-id="0d374-113">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>

3. <span data-ttu-id="0d374-114">Znajdź **\<security>** element z atrybutem **mode** ( **\<security mode =**`MessageOrTransport`**>** gdzie `MessageOrTransport` jest ustawiony jeden z trybów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="0d374-114">Find the **\<security>** element with the **mode** attribute (**\<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>

4. <span data-ttu-id="0d374-115">Znajdź element podrzędny, który jest zgodny z wartością trybu.</span><span class="sxs-lookup"><span data-stu-id="0d374-115">Find the child element that matches the mode value.</span></span> <span data-ttu-id="0d374-116">Na przykład, jeśli tryb jest ustawiony na **komunikat**, Znajdź **\<message>** element zawarty w **\<security>** elemencie.</span><span class="sxs-lookup"><span data-stu-id="0d374-116">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>

5. <span data-ttu-id="0d374-117">Zwróć uwagę na wartość przypisaną do atrybutu **ClientCredentialType** .</span><span class="sxs-lookup"><span data-stu-id="0d374-117">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="0d374-118">Rzeczywista wartość zależy od tego, który tryb jest używany, transport lub wiadomość.</span><span class="sxs-lookup"><span data-stu-id="0d374-118">The actual value depends on which mode is used, transport or message.</span></span>

<span data-ttu-id="0d374-119">Poniższy kod XML przedstawia konfigurację klienta przy użyciu zabezpieczeń komunikatów i wymaga certyfikatu do uwierzytelnienia klienta.</span><span class="sxs-lookup"><span data-stu-id="0d374-119">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="0d374-120">Przykład: Tryb transportu TCP z certyfikatem jako poświadczenia klienta</span><span class="sxs-lookup"><span data-stu-id="0d374-120">Example: TCP Transport Mode with Certificate as Client Credential</span></span>

<span data-ttu-id="0d374-121">Ten przykład ustawia tryb zabezpieczeń na transport i ustawia wartość poświadczeń klienta na certyfikat X. 509.</span><span class="sxs-lookup"><span data-stu-id="0d374-121">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="0d374-122">W poniższych procedurach pokazano, jak ustawić wartość poświadczenia klienta na kliencie w kodzie i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0d374-122">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="0d374-123">Przyjęto założenie, że użyto [Narzędzia do obsługi metadanych ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) do zwrócenia metadanych (kodu i konfiguracji) z usługi.</span><span class="sxs-lookup"><span data-stu-id="0d374-123">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="0d374-124">Aby uzyskać więcej informacji, zobacz [How to: Create a Client](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="0d374-124">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="0d374-125">Aby określić wartość poświadczeń klienta w kodzie</span><span class="sxs-lookup"><span data-stu-id="0d374-125">To specify the client credential value on the client in code</span></span>

1. <span data-ttu-id="0d374-126">Użyj narzędzia do obsługi [metadanych ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , aby wygenerować kod i konfigurację z usługi.</span><span class="sxs-lookup"><span data-stu-id="0d374-126">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>

2. <span data-ttu-id="0d374-127">Utwórz wystąpienie klienta WCF przy użyciu wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="0d374-127">Create an instance of the WCF client using the generated code.</span></span>

3. <span data-ttu-id="0d374-128">W klasie Client Ustaw <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Właściwość <xref:System.ServiceModel.ClientBase%601> klasy na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="0d374-128">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="0d374-129">Ten przykład ustawia właściwość na certyfikat X. 509 przy użyciu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> klasy.</span><span class="sxs-lookup"><span data-stu-id="0d374-129">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     <span data-ttu-id="0d374-130">Można użyć dowolnego wyliczenia <xref:System.Security.Cryptography.X509Certificates.X509FindType> klasy.</span><span class="sxs-lookup"><span data-stu-id="0d374-130">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="0d374-131">Nazwa podmiotu jest używana w tym miejscu w przypadku zmiany certyfikatu (z powodu daty wygaśnięcia).</span><span class="sxs-lookup"><span data-stu-id="0d374-131">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="0d374-132">Użycie nazwy podmiotu umożliwia ponowne znalezienie certyfikatu przez infrastrukturę.</span><span class="sxs-lookup"><span data-stu-id="0d374-132">Using the subject name enables the infrastructure to find the certificate again.</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="0d374-133">Aby określić wartość poświadczenia klienta w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0d374-133">To specify the client credential value on the client in configuration</span></span>

1. <span data-ttu-id="0d374-134">Dodaj [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element do [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="0d374-134">Add a [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

2. <span data-ttu-id="0d374-135">Dodaj [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element do [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="0d374-135">Add a [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="0d374-136">Upewnij się, że atrybut wymagany jest ustawiony `name` na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="0d374-136">Be sure to set the required `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="0d374-137">Dodaj [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element do [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="0d374-137">Add a [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>

4. <span data-ttu-id="0d374-138">Ustaw następujące atrybuty na odpowiednie wartości: `storeLocation` , `storeName` , `x509FindType` , i `findValue` , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0d374-138">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="0d374-139">Aby uzyskać więcej informacji o certyfikatach, zobacz [Praca z certyfikatami](./feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="0d374-139">For more information about certificates, see [Working with Certificates](./feature-details/working-with-certificates.md).</span></span>

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

5. <span data-ttu-id="0d374-140">Podczas konfigurowania klienta należy określić zachowanie, ustawiając `behaviorConfiguration` atrybut `<endpoint>` elementu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0d374-140">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="0d374-141">Element Endpoint jest elementem podrzędnym [\<client>](../configure-apps/file-schema/wcf/client.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="0d374-141">The endpoint element is a child of the [\<client>](../configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="0d374-142">Ponadto Określ nazwę konfiguracji powiązania przez ustawienie `bindingConfiguration` atrybutu na powiązanie dla klienta.</span><span class="sxs-lookup"><span data-stu-id="0d374-142">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="0d374-143">Jeśli używasz wygenerowanego pliku konfiguracji, nazwa powiązania jest generowana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="0d374-143">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="0d374-144">W tym przykładzie nazwa jest `"tcpBindingWithCredential"` .</span><span class="sxs-lookup"><span data-stu-id="0d374-144">In this example, the name is `"tcpBindingWithCredential"`.</span></span>

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a><span data-ttu-id="0d374-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d374-145">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="0d374-146">Programowanie zabezpieczeń WCF</span><span class="sxs-lookup"><span data-stu-id="0d374-146">Programming WCF Security</span></span>](./feature-details/programming-wcf-security.md)
- [<span data-ttu-id="0d374-147">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="0d374-147">Selecting a Credential Type</span></span>](./feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="0d374-148">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="0d374-148">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="0d374-149">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="0d374-149">Working with Certificates</span></span>](./feature-details/working-with-certificates.md)
- [<span data-ttu-id="0d374-150">Instrukcje: tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="0d374-150">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message>](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md)
