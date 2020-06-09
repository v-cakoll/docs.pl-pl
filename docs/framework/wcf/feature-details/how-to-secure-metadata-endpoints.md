---
title: 'Instrukcje: Bezpieczne punkty końcowe metadanych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: c5efd921d3826ef814bf45d6895255981101d992
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592960"
---
# <a name="how-to-secure-metadata-endpoints"></a><span data-ttu-id="bde02-102">Instrukcje: Bezpieczne punkty końcowe metadanych</span><span class="sxs-lookup"><span data-stu-id="bde02-102">How to: Secure Metadata Endpoints</span></span>

<span data-ttu-id="bde02-103">Metadane usługi mogą zawierać poufne informacje o aplikacji, których może użyć złośliwy użytkownik.</span><span class="sxs-lookup"><span data-stu-id="bde02-103">Metadata for a service can contain sensitive information about your application that a malicious user can leverage.</span></span> <span data-ttu-id="bde02-104">Konsumenci usługi mogą również wymagać bezpiecznego mechanizmu uzyskiwania metadanych dotyczących usługi.</span><span class="sxs-lookup"><span data-stu-id="bde02-104">Consumers of your service may also require a secure mechanism for obtaining metadata about your service.</span></span> <span data-ttu-id="bde02-105">W związku z tym czasami konieczne jest opublikowanie metadanych przy użyciu bezpiecznego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="bde02-105">Therefore, it is sometimes necessary to publish your metadata using a secure endpoint.</span></span>

<span data-ttu-id="bde02-106">Punkty końcowe metadanych są zwykle zabezpieczone przy użyciu standardowych mechanizmów zabezpieczeń zdefiniowanych w Windows Communication Foundation (WCF) do zabezpieczania punktów końcowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bde02-106">Metadata endpoints are generally secured using the standard security mechanisms defined in Windows Communication Foundation (WCF) for securing application endpoints.</span></span> <span data-ttu-id="bde02-107">Aby uzyskać więcej informacji, zobacz [Omówienie zabezpieczeń](security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bde02-107">For more information, see [Security Overview](security-overview.md).</span></span>

<span data-ttu-id="bde02-108">W tym temacie przedstawiono procedurę tworzenia punktu końcowego zabezpieczonego za pomocą certyfikatu SSL (SSL) lub innych słów — punktu końcowego HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bde02-108">This topic walks through the steps to create an endpoint secured by a Secure Sockets Layer (SSL) certificate or, in other words, an HTTPS endpoint.</span></span>

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a><span data-ttu-id="bde02-109">Aby utworzyć bezpieczny punkt końcowy metadanych GET HTTPS w kodzie</span><span class="sxs-lookup"><span data-stu-id="bde02-109">To create a secure HTTPS GET metadata endpoint in code</span></span>

1. <span data-ttu-id="bde02-110">Skonfiguruj port przy użyciu odpowiedniego certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="bde02-110">Configure a port with an appropriate X.509 certificate.</span></span> <span data-ttu-id="bde02-111">Certyfikat musi pochodzić z zaufanego urzędu i musi mieć zamierzone użycie "Autoryzacja usługi".</span><span class="sxs-lookup"><span data-stu-id="bde02-111">The certificate must come from a trusted authority, and it must have an intended use of "Service Authorization."</span></span> <span data-ttu-id="bde02-112">Aby dołączyć certyfikat do portu, należy użyć narzędzia HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="bde02-112">You must use the HttpCfg.exe tool to attach the certificate to the port.</span></span> <span data-ttu-id="bde02-113">Zobacz [jak: Konfigurowanie portu z certyfikatem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="bde02-113">See [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="bde02-114">Podmiot certyfikatu lub jego system nazw domen (DNS) musi być zgodny z nazwą komputera.</span><span class="sxs-lookup"><span data-stu-id="bde02-114">The subject of the certificate or its Domain Name System (DNS) must match the name of the computer.</span></span> <span data-ttu-id="bde02-115">Jest to niezbędne, ponieważ jeden z pierwszych kroków wykonywanych przez mechanizm HTTPS polega na sprawdzeniu, czy certyfikat jest wystawiony dla tego samego Uniform Resource Identifier (URI), co adres, na którym jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="bde02-115">This is essential because one of the first steps the HTTPS mechanism performs is to check that the certificate is issued to the same Uniform Resource Identifier (URI) as the address upon which it is invoked.</span></span>

2. <span data-ttu-id="bde02-116">Utwórz nowe wystąpienie <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy.</span><span class="sxs-lookup"><span data-stu-id="bde02-116">Create a new instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class.</span></span>

3. <span data-ttu-id="bde02-117">Ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> Właściwość <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy na `true` .</span><span class="sxs-lookup"><span data-stu-id="bde02-117">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> property of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class to `true`.</span></span>

4. <span data-ttu-id="bde02-118">Ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> Właściwość na odpowiedni adres URL.</span><span class="sxs-lookup"><span data-stu-id="bde02-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> property to an appropriate URL.</span></span> <span data-ttu-id="bde02-119">Należy pamiętać, że jeśli określisz adres bezwzględny, adres URL musi rozpoczynać się od schematu `https://` .</span><span class="sxs-lookup"><span data-stu-id="bde02-119">Note that if you specify an absolute address, the URL must begin with the scheme `https://`.</span></span> <span data-ttu-id="bde02-120">W przypadku określenia adresu względnego należy podać adres podstawowy HTTPS dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="bde02-120">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="bde02-121">Jeśli ta właściwość nie jest ustawiona, adres domyślny to "", lub bezpośrednio z adresem podstawowym HTTPS usługi.</span><span class="sxs-lookup"><span data-stu-id="bde02-121">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

5. <span data-ttu-id="bde02-122">Dodaj wystąpienie do kolekcji zachowań, która <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> <xref:System.ServiceModel.Description.ServiceDescription> zwraca właściwość klasy, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="bde02-122">Add the instance to the behaviors collection that the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property of the <xref:System.ServiceModel.Description.ServiceDescription> class returns, as shown in the following code.</span></span>

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a><span data-ttu-id="bde02-123">Aby utworzyć bezpieczny punkt końcowy metadanych GET HTTPS w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bde02-123">To create a secure HTTPS GET metadata endpoint in configuration</span></span>

1. <span data-ttu-id="bde02-124">Dodaj [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element do [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) elementu pliku konfiguracji dla usługi.</span><span class="sxs-lookup"><span data-stu-id="bde02-124">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element of the configuration file for your service.</span></span>

2. <span data-ttu-id="bde02-125">Dodaj [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) element do [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="bde02-125">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) element to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

3. <span data-ttu-id="bde02-126">Dodaj [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element do `<serviceBehaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="bde02-126">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element to the `<serviceBehaviors>` element.</span></span>

4. <span data-ttu-id="bde02-127">Ustaw `name` atrybut `<behavior>` elementu na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="bde02-127">Set the `name` attribute of the `<behavior>` element to an appropriate value.</span></span> <span data-ttu-id="bde02-128">`name` Atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="bde02-128">The `name` attribute is required.</span></span> <span data-ttu-id="bde02-129">W poniższym przykładzie zastosowano wartość `mySvcBehavior` .</span><span class="sxs-lookup"><span data-stu-id="bde02-129">The example below uses the value `mySvcBehavior`.</span></span>

5. <span data-ttu-id="bde02-130">Dodaj [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) `<behavior>` element do elementu.</span><span class="sxs-lookup"><span data-stu-id="bde02-130">Add a [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) to the `<behavior>` element.</span></span>

6. <span data-ttu-id="bde02-131">Ustaw atrybut `httpsGetEnabled` elementu `<serviceMetadata>` na `true`.</span><span class="sxs-lookup"><span data-stu-id="bde02-131">Set the `httpsGetEnabled` attribute of the `<serviceMetadata>` element to `true`.</span></span>

7. <span data-ttu-id="bde02-132">Ustaw `httpsGetUrl` atrybut `<serviceMetadata>` elementu na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="bde02-132">Set the `httpsGetUrl` attribute of the `<serviceMetadata>` element to an appropriate value.</span></span> <span data-ttu-id="bde02-133">Należy pamiętać, że jeśli określisz adres bezwzględny, adres URL musi rozpoczynać się od schematu `https://` .</span><span class="sxs-lookup"><span data-stu-id="bde02-133">Note that if you specify an absolute address, the URL must begin with the scheme `https://`.</span></span> <span data-ttu-id="bde02-134">W przypadku określenia adresu względnego należy podać adres podstawowy HTTPS dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="bde02-134">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="bde02-135">Jeśli ta właściwość nie jest ustawiona, adres domyślny to "", lub bezpośrednio z adresem podstawowym HTTPS usługi.</span><span class="sxs-lookup"><span data-stu-id="bde02-135">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

8. <span data-ttu-id="bde02-136">Aby użyć zachowania z usługą, należy ustawić `behaviorConfiguration` atrybut [\<service>](../../configure-apps/file-schema/wcf/service.md) elementu na wartość atrybutu nazwy elementu Behavior.</span><span class="sxs-lookup"><span data-stu-id="bde02-136">To use the behavior with a service, set the `behaviorConfiguration` attribute of the [\<service>](../../configure-apps/file-schema/wcf/service.md) element to the value of the name attribute of the behavior element.</span></span> <span data-ttu-id="bde02-137">Poniższy kod konfiguracji pokazuje kompletny przykład.</span><span class="sxs-lookup"><span data-stu-id="bde02-137">The following configuration code shows a complete example.</span></span>

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

## <a name="example"></a><span data-ttu-id="bde02-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="bde02-138">Example</span></span>

<span data-ttu-id="bde02-139">Poniższy przykład tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> klasy i dodaje punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="bde02-139">The following example creates an instance of a <xref:System.ServiceModel.ServiceHost> class and adds an endpoint.</span></span> <span data-ttu-id="bde02-140">Następnie kod tworzy wystąpienie <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy i ustawia właściwości do tworzenia bezpiecznego punktu wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="bde02-140">The code then creates an instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class and sets the properties to create a secure metadata exchange point.</span></span>

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="bde02-141">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="bde02-141">Compiling the Code</span></span>

<span data-ttu-id="bde02-142">W przykładzie kodu są stosowane następujące przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="bde02-142">The code example uses the following namespaces:</span></span>

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a><span data-ttu-id="bde02-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bde02-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [<span data-ttu-id="bde02-144">Instrukcje: konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="bde02-144">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="bde02-145">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="bde02-145">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="bde02-146">Zagadnienia dotyczące zabezpieczeń obejmujące metadane</span><span class="sxs-lookup"><span data-stu-id="bde02-146">Security Considerations with Metadata</span></span>](security-considerations-with-metadata.md)
- [<span data-ttu-id="bde02-147">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="bde02-147">Securing Services and Clients</span></span>](securing-services-and-clients.md)
