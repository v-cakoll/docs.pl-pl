---
title: 'Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: db6bca8728789879f9bfea40904bfc80352d1dbe
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144919"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a><span data-ttu-id="7deb8-102">Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="7deb8-102">How to: Publish Metadata for a Service Using Code</span></span>
<span data-ttu-id="7deb8-103">Jest to jeden z dwóch tematów, które omawiają Publikowanie metadanych dla usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7deb8-103">This is one of two how-to topics that discuss publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="7deb8-104">Istnieją dwa sposoby, aby określić, w jaki sposób usługa powinna publikować metadane przy użyciu pliku konfiguracji i przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="7deb8-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="7deb8-105">W tym temacie przedstawiono sposób publikowania metadanych dla usługi przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="7deb8-105">This topic shows how to publish metadata for a service using a code.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="7deb8-106">W tym temacie przedstawiono sposób publikowania metadanych w niezabezpieczony sposób.</span><span class="sxs-lookup"><span data-stu-id="7deb8-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="7deb8-107">Dowolny klient może pobrać metadane z usługi.</span><span class="sxs-lookup"><span data-stu-id="7deb8-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="7deb8-108">Jeśli wymagasz, aby usługa opublikowała metadane w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="7deb8-108">If you require your service to publish metadata in a secure manner.</span></span> <span data-ttu-id="7deb8-109">Zobacz [Niestandardowy bezpieczny punkt końcowy metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="7deb8-109">see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="7deb8-110">Aby uzyskać więcej informacji na temat publikowania metadanych w pliku konfiguracji, zobacz [How to: Publikowanie metadanych dla usługi za pomocą pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="7deb8-110">For more information about publishing metadata in a configuration file, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span> <span data-ttu-id="7deb8-111">Publikowanie metadanych umożliwia klientom Pobieranie metadanych przy użyciu żądania GET WS-transfer lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="7deb8-111">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="7deb8-112">Aby upewnić się, że kod działa, należy utworzyć podstawową usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="7deb8-112">To be sure that the code is working you must create a basic WCF service.</span></span> <span data-ttu-id="7deb8-113">W poniższym kodzie znajduje się podstawowa usługa samodzielna.</span><span class="sxs-lookup"><span data-stu-id="7deb8-113">A basic self-hosted service is provided in the following code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a><span data-ttu-id="7deb8-114">Aby opublikować metadane w kodzie</span><span class="sxs-lookup"><span data-stu-id="7deb8-114">To publish metadata in code</span></span>  
  
1. <span data-ttu-id="7deb8-115">W ramach głównej metody aplikacji konsolowej Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> obiektu przez przekazanie go do typu usługi i adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="7deb8-115">Within the main method of a console application, instantiate a <xref:System.ServiceModel.ServiceHost> object by passing in the service type and the base address.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. <span data-ttu-id="7deb8-116">Utwórz blok try bezpośrednio poniżej kodu dla kroku 1, który przechwytuje wszystkie wyjątki, które są zgłaszane podczas działania usługi.</span><span class="sxs-lookup"><span data-stu-id="7deb8-116">Create a try block immediately below the code for step 1, this catches any exceptions that get thrown while the service is running.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. <span data-ttu-id="7deb8-117">Sprawdź, czy host usługi zawiera już <xref:System.ServiceModel.Description.ServiceMetadataBehavior> , jeśli nie, Utwórz nowe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="7deb8-117">Check to see whether the service host already contains a <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, if not, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. <span data-ttu-id="7deb8-118">Ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> Właściwość na`true.`</span><span class="sxs-lookup"><span data-stu-id="7deb8-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true.`</span></span>  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. <span data-ttu-id="7deb8-119"><xref:System.ServiceModel.Description.ServiceMetadataBehavior>Zawiera <xref:System.ServiceModel.Description.MetadataExporter> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="7deb8-119">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contains a <xref:System.ServiceModel.Description.MetadataExporter> property.</span></span> <span data-ttu-id="7deb8-120"><xref:System.ServiceModel.Description.MetadataExporter>Zawiera <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="7deb8-120">The <xref:System.ServiceModel.Description.MetadataExporter> contains a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property.</span></span> <span data-ttu-id="7deb8-121">Ustaw wartość <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> właściwości na <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> .</span><span class="sxs-lookup"><span data-stu-id="7deb8-121">Set the value of the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span></span> <span data-ttu-id="7deb8-122"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A>Właściwość można również ustawić na <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> .</span><span class="sxs-lookup"><span data-stu-id="7deb8-122">The <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property can also be set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span></span> <span data-ttu-id="7deb8-123">Po ustawieniu na wartość w <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> polu Eksport metadanych są generowane informacje o zasadach z metadanymi, które są zgodne z usługą ws-policy 1,5.</span><span class="sxs-lookup"><span data-stu-id="7deb8-123">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> the metadata exporter generates policy information with the metadata that" conforms to WS-Policy 1.5.</span></span> <span data-ttu-id="7deb8-124">Gdy jest ustawiony na <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> Eksport metadanych, są generowane informacje o zasadach, które są zgodne z usługą ws-policy 1,2.</span><span class="sxs-lookup"><span data-stu-id="7deb8-124">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> the metadata exporter generates policy information that conforms to WS-Policy 1.2.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. <span data-ttu-id="7deb8-125">Dodaj <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie do kolekcji zachowań hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="7deb8-125">Add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance to the service host's behaviors collection.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. <span data-ttu-id="7deb8-126">Dodaj punkt końcowy wymiany metadanych do hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="7deb8-126">Add the metadata exchange endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. <span data-ttu-id="7deb8-127">Dodaj punkt końcowy aplikacji do hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="7deb8-127">Add an application endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    > <span data-ttu-id="7deb8-128">Jeśli nie dodasz żadnych punktów końcowych do usługi, środowisko uruchomieniowe doda domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="7deb8-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="7deb8-129">W tym przykładzie, ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ustawiony na `true` , usługa ma włączone metadane publikowania.</span><span class="sxs-lookup"><span data-stu-id="7deb8-129">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, the service has publishing metadata enabled.</span></span> <span data-ttu-id="7deb8-130">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7deb8-130">For more information about default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="7deb8-131">Otwórz hosta usługi i poczekaj na wywołania przychodzące.</span><span class="sxs-lookup"><span data-stu-id="7deb8-131">Open the service host and wait for incoming calls.</span></span> <span data-ttu-id="7deb8-132">Gdy użytkownik naciśnie klawisz ENTER, Zamknij hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="7deb8-132">When the user presses ENTER, close the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. <span data-ttu-id="7deb8-133">Skompiluj i uruchom aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="7deb8-133">Build and run the console application.</span></span>  
  
11. <span data-ttu-id="7deb8-134">Użyj programu Internet Explorer, aby przejść do adresu podstawowego usługi ( `http://localhost:8001/MetadataSample` w tym przykładzie) i sprawdzić, czy Publikowanie metadanych jest włączone.</span><span class="sxs-lookup"><span data-stu-id="7deb8-134">Use Internet Explorer to browse to the base address of the service (`http://localhost:8001/MetadataSample` in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="7deb8-135">Powinna zostać wyświetlona strona sieci Web informująca o "prostej usłudze" u góry i bezpośrednio poniżej "została utworzona usługa".</span><span class="sxs-lookup"><span data-stu-id="7deb8-135">You should see a Web page displayed that says "Simple Service" at the top and immediately below "You have created a service."</span></span> <span data-ttu-id="7deb8-136">Jeśli nie, zostanie wyświetlony komunikat w górnej części strony wyników: "Publikowanie metadanych dla tej usługi jest obecnie wyłączone".</span><span class="sxs-lookup"><span data-stu-id="7deb8-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
## <a name="example"></a><span data-ttu-id="7deb8-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="7deb8-137">Example</span></span>  
 <span data-ttu-id="7deb8-138">Poniższy przykład kodu przedstawia implementację podstawowej usługi WCF, która publikuje metadane dla usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7deb8-138">The following code example shows the implementation of a basic WCF service that publishes metadata for the service in code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="7deb8-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7deb8-139">See also</span></span>

- [<span data-ttu-id="7deb8-140">Instrukcje: hostowanie usługi WCF w zarządzanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="7deb8-140">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="7deb8-141">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="7deb8-141">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="7deb8-142">Przegląd architektury metadanych</span><span class="sxs-lookup"><span data-stu-id="7deb8-142">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="7deb8-143">Używanie metadanych</span><span class="sxs-lookup"><span data-stu-id="7deb8-143">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="7deb8-144">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7deb8-144">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
