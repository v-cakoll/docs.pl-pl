---
title: 'Instrukcje: publikowanie metadanych dla usługi przy użyciu kodu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: 870142724321629d6dbeccd4118b814283901776
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297970"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a><span data-ttu-id="50c93-102">Instrukcje: publikowanie metadanych dla usługi przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="50c93-102">How to: Publish Metadata for a Service Using Code</span></span>
<span data-ttu-id="50c93-103">Jest to jedna z dwóch tematy porad, które mówią o Publikowanie metadanych dla usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="50c93-103">This is one of two how-to topics that discuss publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="50c93-104">Istnieją dwa sposoby, aby określić, jak usługa powinna Publikowanie metadanych, przy użyciu pliku konfiguracji i przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="50c93-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="50c93-105">W tym temacie przedstawiono sposób Publikowanie metadanych dla usługi przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="50c93-105">This topic shows how to publish metadata for a service using a code.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="50c93-106">W tym temacie przedstawiono sposób Publikowanie metadanych w niezabezpieczony sposób.</span><span class="sxs-lookup"><span data-stu-id="50c93-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="50c93-107">Dowolny klient może pobierać metadanych z usługi.</span><span class="sxs-lookup"><span data-stu-id="50c93-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="50c93-108">Jeśli potrzebujesz usługi w celu publikowania metadanych w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="50c93-108">If you require your service to publish metadata in a secure manner.</span></span> <span data-ttu-id="50c93-109">zobacz [niestandardowy bezpieczny punkt końcowy metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="50c93-109">see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="50c93-110">Aby uzyskać więcej informacji na temat publikowania metadanych w pliku konfiguracji, zobacz [jak: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="50c93-110">For more information about publishing metadata in a configuration file, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span> <span data-ttu-id="50c93-111">Publikowanie metadanych zezwala klientom na pobieranie metadanych za pomocą ROZPOCZYNANIE transferu WS żądania lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="50c93-111">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="50c93-112">Należy upewnić się, że działa kod, możesz utworzyć podstawowe usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="50c93-112">To be sure that the code is working you must create a basic WCF service.</span></span> <span data-ttu-id="50c93-113">Podstawowa usługa Self-Hosted znajduje się w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="50c93-113">A basic self-hosted service is provided in the following code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a><span data-ttu-id="50c93-114">Publikowanie metadanych w kodzie</span><span class="sxs-lookup"><span data-stu-id="50c93-114">To publish metadata in code</span></span>  
  
1. <span data-ttu-id="50c93-115">W metodzie głównej aplikacji konsoli, należy utworzyć wystąpienie <xref:System.ServiceModel.ServiceHost> obiektu, przekazując typ usługi i adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="50c93-115">Within the main method of a console application, instantiate a <xref:System.ServiceModel.ServiceHost> object by passing in the service type and the base address.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. <span data-ttu-id="50c93-116">Tworzenie bloku try bezpośrednio poniżej kodu w kroku 1, to przechwytuje wszystkie wyjątki, które Pobierz zgłaszany, gdy usługa jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="50c93-116">Create a try block immediately below the code for step 1, this catches any exceptions that get thrown while the service is running.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. <span data-ttu-id="50c93-117">Sprawdź, czy host usługi zawiera już <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, jeśli nie, Utwórz nową <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="50c93-117">Check to see whether the service host already contains a <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, if not, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. <span data-ttu-id="50c93-118">Ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwości `true.`</span><span class="sxs-lookup"><span data-stu-id="50c93-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true.`</span></span>  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. <span data-ttu-id="50c93-119"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> Zawiera <xref:System.ServiceModel.Description.MetadataExporter> właściwości.</span><span class="sxs-lookup"><span data-stu-id="50c93-119">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contains a <xref:System.ServiceModel.Description.MetadataExporter> property.</span></span> <span data-ttu-id="50c93-120"><xref:System.ServiceModel.Description.MetadataExporter> Zawiera <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="50c93-120">The <xref:System.ServiceModel.Description.MetadataExporter> contains a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property.</span></span> <span data-ttu-id="50c93-121">Ustaw wartość <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> właściwość <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span><span class="sxs-lookup"><span data-stu-id="50c93-121">Set the value of the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span></span> <span data-ttu-id="50c93-122"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Właściwość można ustawić <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span><span class="sxs-lookup"><span data-stu-id="50c93-122">The <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property can also be set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span></span> <span data-ttu-id="50c93-123">Po ustawieniu <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> eksportu metadanych generuje informacje o zasadach z metadanymi, "jest zgodny do wersji 1.5 usługi WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="50c93-123">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> the metadata exporter generates policy information with the metadata that" conforms to WS-Policy 1.5.</span></span> <span data-ttu-id="50c93-124">Po ustawieniu <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> eksportu metadanych generuje informacje o zasadach, który jest zgodny z 1.2 WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="50c93-124">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> the metadata exporter generates policy information that conforms to WS-Policy 1.2.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. <span data-ttu-id="50c93-125">Dodaj <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie kolekcji zachowań hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="50c93-125">Add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance to the service host's behaviors collection.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. <span data-ttu-id="50c93-126">Dodaj punkt końcowy wymiany metadanych do hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="50c93-126">Add the metadata exchange endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. <span data-ttu-id="50c93-127">Dodawanie punktu końcowego aplikacji do hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="50c93-127">Add an application endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  <span data-ttu-id="50c93-128">Jeśli nie dodasz żadnych punktów końcowych do usługi, środowiska uruchomieniowego dodaje domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="50c93-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="50c93-129">W tym przykładzie ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> równa `true`, usługa ma Publikowanie metadanych włączone.</span><span class="sxs-lookup"><span data-stu-id="50c93-129">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, the service has publishing metadata enabled.</span></span> <span data-ttu-id="50c93-130">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="50c93-130">For more information about default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="50c93-131">Otworzyć hosta usługi i zaczekaj na połączenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="50c93-131">Open the service host and wait for incoming calls.</span></span> <span data-ttu-id="50c93-132">Gdy użytkownik naciśnie klawisz ENTER, zamknij hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="50c93-132">When the user presses ENTER, close the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. <span data-ttu-id="50c93-133">Skompiluj i uruchom aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="50c93-133">Build and run the console application.</span></span>  
  
11. <span data-ttu-id="50c93-134">Aby przejść do podstawowego adresu usługi w programie Internet Explorer (http://localhost:8001/MetadataSample w tym przykładzie) i sprawdź, czy Publikowanie metadanych jest włączona.</span><span class="sxs-lookup"><span data-stu-id="50c93-134">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="50c93-135">Powinien zostać wyświetlony strona sieci Web wyświetlany jest wyświetlany komunikat "Prostą usługę" u góry, a od razu poniżej "Utworzono usługę."</span><span class="sxs-lookup"><span data-stu-id="50c93-135">You should see a Web page displayed that says "Simple Service" at the top and immediately below "You have created a service."</span></span> <span data-ttu-id="50c93-136">W przeciwnym razie komunikat wyświetlany w górnej części strony wynikowy: "Publikowanie metadanych dla tej usługi jest obecnie wyłączona."</span><span class="sxs-lookup"><span data-stu-id="50c93-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
## <a name="example"></a><span data-ttu-id="50c93-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="50c93-137">Example</span></span>  
 <span data-ttu-id="50c93-138">Poniższy przykład kodu pokazuje implementację podstawowej usługi WCF, która umożliwia publikowanie metadanych dla usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="50c93-138">The following code example shows the implementation of a basic WCF service that publishes metadata for the service in code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="50c93-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50c93-139">See also</span></span>

- [<span data-ttu-id="50c93-140">Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="50c93-140">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="50c93-141">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="50c93-141">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="50c93-142">Przegląd architektury metadanych</span><span class="sxs-lookup"><span data-stu-id="50c93-142">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="50c93-143">Używanie metadanych</span><span class="sxs-lookup"><span data-stu-id="50c93-143">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="50c93-144">Instrukcje: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="50c93-144">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
