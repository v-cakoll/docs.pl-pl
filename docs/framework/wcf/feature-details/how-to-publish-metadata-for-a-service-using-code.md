---
title: 'Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu'
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
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c3d2fd1222539ec8017846069e7eda9a2c503f22
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a><span data-ttu-id="42053-102">Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="42053-102">How to: Publish Metadata for a Service Using Code</span></span>
<span data-ttu-id="42053-103">Jest to jeden z dwóch tematy porad dotyczących Publikowanie metadanych dla [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="42053-103">This is one of two how-to topics that discuss publishing metadata for a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="42053-104">Istnieją dwa sposoby, aby określić, jak usługa powinna Publikowanie metadanych, przy użyciu pliku konfiguracji i kod.</span><span class="sxs-lookup"><span data-stu-id="42053-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="42053-105">W tym temacie przedstawiono sposób Publikowanie metadanych dla usługi przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="42053-105">This topic shows how to publish metadata for a service using a code.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="42053-106">W tym temacie pokazano, jak publikować metadane w sposób niezabezpieczonych.</span><span class="sxs-lookup"><span data-stu-id="42053-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="42053-107">Dowolny klient może pobrać metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="42053-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="42053-108">Jeśli wymagana jest usługa Publikowanie metadanych w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="42053-108">If you require your service to publish metadata in a secure manner.</span></span> <span data-ttu-id="42053-109">zobacz [punktu końcowego metadanych niestandardowy bezpieczny](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="42053-109">see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="42053-110">Aby uzyskać więcej informacji o publikowaniu metadanych w pliku konfiguracji, zobacz [porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="42053-110">For more information about publishing metadata in a configuration file, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span> <span data-ttu-id="42053-111">Publikowanie metadanych pozwala klientom na pobieranie metadanych za pomocą żądania GET usługi WS-Transfer lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="42053-111">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="42053-112">Należy upewnić się, że kod działa można utworzyć podstawowej usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="42053-112">To be sure that the code is working you must create a basic WCF service.</span></span> <span data-ttu-id="42053-113">Podstawowa usługa hostowania samoobsługowego jest dostarczana w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="42053-113">A basic self-hosted service is provided in the following code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a><span data-ttu-id="42053-114">Publikowanie metadanych w kodzie</span><span class="sxs-lookup"><span data-stu-id="42053-114">To publish metadata in code</span></span>  
  
1.  <span data-ttu-id="42053-115">W metodzie głównego aplikacji konsoli wystąpienia <xref:System.ServiceModel.ServiceHost> obiektu przez przekazywanie typu usługi i adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="42053-115">Within the main method of a console application, instantiate a <xref:System.ServiceModel.ServiceHost> object by passing in the service type and the base address.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2.  <span data-ttu-id="42053-116">Tworzenie bloku try bezpośrednio pod kodu w kroku 1, to przechwytuje wszystkie wyjątki, które uzyskać zgłoszony, gdy usługa jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="42053-116">Create a try block immediately below the code for step 1, this catches any exceptions that get thrown while the service is running.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3.  <span data-ttu-id="42053-117">Sprawdź, czy host usługi zawiera już <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, jeśli nie, Utwórz nową <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="42053-117">Check to see whether the service host already contains a <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, if not, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4.  <span data-ttu-id="42053-118">Ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwości `true.`</span><span class="sxs-lookup"><span data-stu-id="42053-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true.`</span></span>  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5.  <span data-ttu-id="42053-119"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> Zawiera <xref:System.ServiceModel.Description.MetadataExporter> właściwości.</span><span class="sxs-lookup"><span data-stu-id="42053-119">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contains a <xref:System.ServiceModel.Description.MetadataExporter> property.</span></span> <span data-ttu-id="42053-120"><xref:System.ServiceModel.Description.MetadataExporter> Zawiera <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="42053-120">The <xref:System.ServiceModel.Description.MetadataExporter> contains a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property.</span></span> <span data-ttu-id="42053-121">Ustaw wartość <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> właściwości <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span><span class="sxs-lookup"><span data-stu-id="42053-121">Set the value of the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span></span> <span data-ttu-id="42053-122"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Można również ustawić właściwość <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span><span class="sxs-lookup"><span data-stu-id="42053-122">The <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property can also be set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span></span> <span data-ttu-id="42053-123">Jeśli wartość <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> eksportu metadanych generuje informacje o zasadach z metadanymi który "odpowiada 1.5 WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="42053-123">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> the metadata exporter generates policy information with the metadata that" conforms to WS-Policy 1.5.</span></span> <span data-ttu-id="42053-124">Jeśli wartość <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> eksportu metadanych generuje informacje o zasadach, które odpowiada 1.2 WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="42053-124">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> the metadata exporter generates policy information that conforms to WS-Policy 1.2.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6.  <span data-ttu-id="42053-125">Dodaj <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie do kolekcji zachowań hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="42053-125">Add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance to the service host's behaviors collection.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7.  <span data-ttu-id="42053-126">Dodaj punkt końcowy wymiany metadanych do hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="42053-126">Add the metadata exchange endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8.  <span data-ttu-id="42053-127">Dodaj punkt końcowy aplikacji do usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="42053-127">Add an application endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  <span data-ttu-id="42053-128">Jeśli nie dodawaj żadnych punktów końcowych do usługi, środowisko uruchomieniowe dodaje domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="42053-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="42053-129">W tym przykładzie ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ustawioną `true`, usługa ma Publikowanie metadanych włączone.</span><span class="sxs-lookup"><span data-stu-id="42053-129">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, the service has publishing metadata enabled.</span></span> <span data-ttu-id="42053-130">Aby uzyskać więcej informacji o domyślnych punktów końcowych, zobacz [uproszczony konfiguracji](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="42053-130">For more information about default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="42053-131">Otworzyć hosta usługi, a następnie zaczekaj na połączenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="42053-131">Open the service host and wait for incoming calls.</span></span> <span data-ttu-id="42053-132">Gdy użytkownik naciśnie ENTER, zamknij hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="42053-132">When the user presses ENTER, close the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. <span data-ttu-id="42053-133">Tworzenie i uruchamianie aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="42053-133">Build and run the console application.</span></span>  
  
11. <span data-ttu-id="42053-134">Aby przejść do podstawowego adresu usługi w programie Internet Explorer (http://localhost:8001/MetadataSample w tym przykładzie) i sprawdź, czy Publikowanie metadanych jest włączony.</span><span class="sxs-lookup"><span data-stu-id="42053-134">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="42053-135">Powinna zostać wyświetlona strona sieci Web wyświetlane, stwierdzający "Simple Service" u góry i natychmiast poniżej "Utworzono usługę."</span><span class="sxs-lookup"><span data-stu-id="42053-135">You should see a Web page displayed that says "Simple Service" at the top and immediately below "You have created a service."</span></span> <span data-ttu-id="42053-136">Jeśli nie, zostanie wyświetlony komunikat w górnej części strony wynikowy: "Publikowanie metadanych dla tej usługi jest obecnie wyłączona."</span><span class="sxs-lookup"><span data-stu-id="42053-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
## <a name="example"></a><span data-ttu-id="42053-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="42053-137">Example</span></span>  
 <span data-ttu-id="42053-138">Poniższy przykładowy kod przedstawia implementację podstawowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, która umożliwia publikowanie metadanych dla usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="42053-138">The following code example shows the implementation of a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that publishes metadata for the service in code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="42053-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42053-139">See Also</span></span>  
 [<span data-ttu-id="42053-140">Instrukcje: hostowanie usługi WCF w zarządzanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="42053-140">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [<span data-ttu-id="42053-141">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="42053-141">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="42053-142">Przegląd architektury metadanych</span><span class="sxs-lookup"><span data-stu-id="42053-142">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [<span data-ttu-id="42053-143">Używanie metadanych</span><span class="sxs-lookup"><span data-stu-id="42053-143">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [<span data-ttu-id="42053-144">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="42053-144">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
