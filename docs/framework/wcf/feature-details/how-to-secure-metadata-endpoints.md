---
title: 'Instrukcje: bezpieczne punkty końcowe metadanych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: ee64e53f49e15059c91982f2e64879b9f4c76d78
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834677"
---
# <a name="how-to-secure-metadata-endpoints"></a><span data-ttu-id="1585b-102">Instrukcje: bezpieczne punkty końcowe metadanych</span><span class="sxs-lookup"><span data-stu-id="1585b-102">How to: Secure Metadata Endpoints</span></span>

<span data-ttu-id="1585b-103">Metadane usługi mogą zawierać poufne informacje o aplikacji, których może użyć złośliwy użytkownik.</span><span class="sxs-lookup"><span data-stu-id="1585b-103">Metadata for a service can contain sensitive information about your application that a malicious user can leverage.</span></span> <span data-ttu-id="1585b-104">Konsumenci usługi mogą również wymagać bezpiecznego mechanizmu uzyskiwania metadanych dotyczących usługi.</span><span class="sxs-lookup"><span data-stu-id="1585b-104">Consumers of your service may also require a secure mechanism for obtaining metadata about your service.</span></span> <span data-ttu-id="1585b-105">W związku z tym czasami konieczne jest opublikowanie metadanych przy użyciu bezpiecznego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1585b-105">Therefore, it is sometimes necessary to publish your metadata using a secure endpoint.</span></span>

<span data-ttu-id="1585b-106">Punkty końcowe metadanych są zwykle zabezpieczone przy użyciu standardowych mechanizmów zabezpieczeń zdefiniowanych w Windows Communication Foundation (WCF) do zabezpieczania punktów końcowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1585b-106">Metadata endpoints are generally secured using the standard security mechanisms defined in Windows Communication Foundation (WCF) for securing application endpoints.</span></span> <span data-ttu-id="1585b-107">Aby uzyskać więcej informacji, zobacz [Omówienie zabezpieczeń](security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1585b-107">For more information, see [Security Overview](security-overview.md).</span></span>

<span data-ttu-id="1585b-108">W tym temacie przedstawiono procedurę tworzenia punktu końcowego zabezpieczonego za pomocą certyfikatu SSL (SSL) lub innych słów — punktu końcowego HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1585b-108">This topic walks through the steps to create an endpoint secured by a Secure Sockets Layer (SSL) certificate or, in other words, an HTTPS endpoint.</span></span>

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a><span data-ttu-id="1585b-109">Aby utworzyć bezpieczny punkt końcowy metadanych GET HTTPS w kodzie</span><span class="sxs-lookup"><span data-stu-id="1585b-109">To create a secure HTTPS GET metadata endpoint in code</span></span>

1. <span data-ttu-id="1585b-110">Skonfiguruj port przy użyciu odpowiedniego certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="1585b-110">Configure a port with an appropriate X.509 certificate.</span></span> <span data-ttu-id="1585b-111">Certyfikat musi pochodzić z zaufanego urzędu i musi mieć zamierzone użycie "Autoryzacja usługi".</span><span class="sxs-lookup"><span data-stu-id="1585b-111">The certificate must come from a trusted authority, and it must have an intended use of "Service Authorization."</span></span> <span data-ttu-id="1585b-112">Aby dołączyć certyfikat do portu, należy użyć narzędzia HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="1585b-112">You must use the HttpCfg.exe tool to attach the certificate to the port.</span></span> <span data-ttu-id="1585b-113">Zobacz [jak: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="1585b-113">See [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="1585b-114">Podmiot certyfikatu lub jego system nazw domen (DNS) musi być zgodny z nazwą komputera.</span><span class="sxs-lookup"><span data-stu-id="1585b-114">The subject of the certificate or its Domain Name System (DNS) must match the name of the computer.</span></span> <span data-ttu-id="1585b-115">Jest to niezbędne, ponieważ jeden z pierwszych kroków wykonywanych przez mechanizm HTTPS polega na sprawdzeniu, czy certyfikat jest wystawiony dla tego samego Uniform Resource Identifier (URI), co adres, na którym jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="1585b-115">This is essential because one of the first steps the HTTPS mechanism performs is to check that the certificate is issued to the same Uniform Resource Identifier (URI) as the address upon which it is invoked.</span></span>

2. <span data-ttu-id="1585b-116">Utwórz nowe wystąpienie klasy <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="1585b-116">Create a new instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class.</span></span>

3. <span data-ttu-id="1585b-117">Ustaw właściwość <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> klasy <xref:System.ServiceModel.Description.ServiceMetadataBehavior> na `true`.</span><span class="sxs-lookup"><span data-stu-id="1585b-117">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> property of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class to `true`.</span></span>

4. <span data-ttu-id="1585b-118">Ustaw właściwość <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> na odpowiedni adres URL.</span><span class="sxs-lookup"><span data-stu-id="1585b-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> property to an appropriate URL.</span></span> <span data-ttu-id="1585b-119">Należy pamiętać, że jeśli określisz adres bezwzględny, adres URL musi rozpoczynać się od schematu "https://".</span><span class="sxs-lookup"><span data-stu-id="1585b-119">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="1585b-120">W przypadku określenia adresu względnego należy podać adres podstawowy HTTPS dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="1585b-120">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="1585b-121">Jeśli ta właściwość nie jest ustawiona, adres domyślny to "", lub bezpośrednio z adresem podstawowym HTTPS usługi.</span><span class="sxs-lookup"><span data-stu-id="1585b-121">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

5. <span data-ttu-id="1585b-122">Dodaj wystąpienie do kolekcji zachowań, która zwraca właściwość <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> klasy <xref:System.ServiceModel.Description.ServiceDescription>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1585b-122">Add the instance to the behaviors collection that the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property of the <xref:System.ServiceModel.Description.ServiceDescription> class returns, as shown in the following code.</span></span>

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a><span data-ttu-id="1585b-123">Aby utworzyć bezpieczny punkt końcowy metadanych GET HTTPS w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1585b-123">To create a secure HTTPS GET metadata endpoint in configuration</span></span>

1. <span data-ttu-id="1585b-124">Dodaj element [\<behaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) do elementu [> \<system. ServiceModel](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) w pliku konfiguracji dla usługi.</span><span class="sxs-lookup"><span data-stu-id="1585b-124">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element of the configuration file for your service.</span></span>

2. <span data-ttu-id="1585b-125">Dodaj element [\<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do elementu [> \<behaviors](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="1585b-125">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

3. <span data-ttu-id="1585b-126">Dodaj element [\<behavior >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) do elementu `<serviceBehaviors>`.</span><span class="sxs-lookup"><span data-stu-id="1585b-126">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element to the `<serviceBehaviors>` element.</span></span>

4. <span data-ttu-id="1585b-127">Dla atrybutu `name` elementu `<behavior>` Ustaw odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="1585b-127">Set the `name` attribute of the `<behavior>` element to an appropriate value.</span></span> <span data-ttu-id="1585b-128">Atrybut `name` jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="1585b-128">The `name` attribute is required.</span></span> <span data-ttu-id="1585b-129">Poniższy przykład używa wartości `mySvcBehavior`.</span><span class="sxs-lookup"><span data-stu-id="1585b-129">The example below uses the value `mySvcBehavior`.</span></span>

5. <span data-ttu-id="1585b-130">Dodaj [> \<serviceMetadata](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) do elementu `<behavior>`.</span><span class="sxs-lookup"><span data-stu-id="1585b-130">Add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) to the `<behavior>` element.</span></span>

6. <span data-ttu-id="1585b-131">Ustaw atrybut `httpsGetEnabled` elementu `<serviceMetadata>` na `true`.</span><span class="sxs-lookup"><span data-stu-id="1585b-131">Set the `httpsGetEnabled` attribute of the `<serviceMetadata>` element to `true`.</span></span>

7. <span data-ttu-id="1585b-132">Dla atrybutu `httpsGetUrl` elementu `<serviceMetadata>` Ustaw odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="1585b-132">Set the `httpsGetUrl` attribute of the `<serviceMetadata>` element to an appropriate value.</span></span> <span data-ttu-id="1585b-133">Należy pamiętać, że jeśli określisz adres bezwzględny, adres URL musi rozpoczynać się od schematu "https://".</span><span class="sxs-lookup"><span data-stu-id="1585b-133">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="1585b-134">W przypadku określenia adresu względnego należy podać adres podstawowy HTTPS dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="1585b-134">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="1585b-135">Jeśli ta właściwość nie jest ustawiona, adres domyślny to "", lub bezpośrednio z adresem podstawowym HTTPS usługi.</span><span class="sxs-lookup"><span data-stu-id="1585b-135">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

8. <span data-ttu-id="1585b-136">Aby użyć zachowania z usługą, należy ustawić atrybut `behaviorConfiguration` elementu [> \<service](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) na wartość atrybutu name elementu Behavior.</span><span class="sxs-lookup"><span data-stu-id="1585b-136">To use the behavior with a service, set the `behaviorConfiguration` attribute of the [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element to the value of the name attribute of the behavior element.</span></span> <span data-ttu-id="1585b-137">Poniższy kod konfiguracji pokazuje kompletny przykład.</span><span class="sxs-lookup"><span data-stu-id="1585b-137">The following configuration code shows a complete example.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
     <system.serviceModel>
      <behaviors>
       <serviceBehaviors>
        <behavior name="mySvcBehavior">
         <serviceMetadata httpsGetEnabled="true"
              httpsGetUrl="https://localhost:8036/calcMetadata" />
        </behavior>
       </serviceBehaviors>
      </behaviors>
     <services>
      <service behaviorConfiguration="mySvcBehavior"
            name="Microsoft.Security.Samples.Calculator">
       <endpoint address="http://localhost:8037/ServiceModelSamples/calculator"
       binding="wsHttpBinding" bindingConfiguration=""
       contract="Microsoft.Security.Samples.ICalculator" />
      </service>
     </services>
    </system.serviceModel>
    </configuration>
    ```

## <a name="example"></a><span data-ttu-id="1585b-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="1585b-138">Example</span></span>

<span data-ttu-id="1585b-139">Poniższy przykład tworzy wystąpienie klasy <xref:System.ServiceModel.ServiceHost> i dodaje punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="1585b-139">The following example creates an instance of a <xref:System.ServiceModel.ServiceHost> class and adds an endpoint.</span></span> <span data-ttu-id="1585b-140">Następnie kod tworzy wystąpienie klasy <xref:System.ServiceModel.Description.ServiceMetadataBehavior> i ustawia właściwości w celu utworzenia bezpiecznego punktu wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="1585b-140">The code then creates an instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class and sets the properties to create a secure metadata exchange point.</span></span>

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="1585b-141">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1585b-141">Compiling the Code</span></span>

<span data-ttu-id="1585b-142">W przykładzie kodu są stosowane następujące przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="1585b-142">The code example uses the following namespaces:</span></span>

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a><span data-ttu-id="1585b-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1585b-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [<span data-ttu-id="1585b-144">Instrukcje: Konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="1585b-144">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="1585b-145">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="1585b-145">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="1585b-146">Zagadnienia dotyczące zabezpieczeń dotyczące metadanych</span><span class="sxs-lookup"><span data-stu-id="1585b-146">Security Considerations with Metadata</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [<span data-ttu-id="1585b-147">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="1585b-147">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
