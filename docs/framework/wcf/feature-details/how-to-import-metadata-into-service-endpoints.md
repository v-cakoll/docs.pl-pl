---
title: 'Instrukcje: Importowanie metadanych do punktów końcowych usług'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b86f31217812767b0fbbd785a0f3ff96c2948854
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="adad5-102">Instrukcje: Importowanie metadanych do punktów końcowych usług</span><span class="sxs-lookup"><span data-stu-id="adad5-102">How to: Import Metadata into Service Endpoints</span></span>
<span data-ttu-id="adad5-103">W tym temacie wyjaśniono, jak zaimportować metadane do kolekcji punktów końcowych usługi i korzystać z usługi zdefiniowane w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="adad5-103">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="adad5-104">W tym temacie przedstawiają sposób tworzenia aplikacji klienckiej, który importuje metadane z usługi, a następnie wywołania `Add` metody dla usługi.</span><span class="sxs-lookup"><span data-stu-id="adad5-104">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="adad5-105">Aby zaimportować metadane do punktów końcowych usług</span><span class="sxs-lookup"><span data-stu-id="adad5-105">To import metadata into service endpoints</span></span>  
  
1.  <span data-ttu-id="adad5-106">Deklarowanie <xref:System.ServiceModel.EndpointAddress> i zainicjować go z identyfikatora URI (Uniform Resource) dla adresu programu exchange (MEX) metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="adad5-106">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2.  <span data-ttu-id="adad5-107">Utwórz <xref:System.ServiceModel.Description.MetadataExchangeClient>, przekazując adresu MEX. i wywołania <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="adad5-107">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="adad5-108">To pobiera metadane z usługi.</span><span class="sxs-lookup"><span data-stu-id="adad5-108">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3.  <span data-ttu-id="adad5-109">Utwórz <xref:System.ServiceModel.Description.WsdlImporter>, przekazując metadanych wcześniej pobrane i wywołania <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span><span class="sxs-lookup"><span data-stu-id="adad5-109">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="adad5-110">Powoduje to kolekcja <xref:System.ServiceModel.Description.ContractDescription> obiektów.</span><span class="sxs-lookup"><span data-stu-id="adad5-110">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="adad5-111">Można także wywołać <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> lub <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="adad5-111">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    >  <span data-ttu-id="adad5-112">Po zaimportowaniu metadanych, nie można utworzyć kanału klienta lub wyeksportować metadane.</span><span class="sxs-lookup"><span data-stu-id="adad5-112">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="adad5-113">Jest to spowodowane typu informacje są niedostępne w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="adad5-113">This is because no type information is available at this point.</span></span> <span data-ttu-id="adad5-114">Informacje o typie jest wymagany do faktycznie interakcji z usługą lub wyeksportować metadane.</span><span class="sxs-lookup"><span data-stu-id="adad5-114">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="adad5-115">Aby wygenerować informacje o typie, należy wygenerować kod wyświetlany w kroku 4 i 5.</span><span class="sxs-lookup"><span data-stu-id="adad5-115">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="adad5-116">Alternatywnie można użyć <xref:System.ServiceModel.Description.MetadataResolver> Klasa pomocy.</span><span class="sxs-lookup"><span data-stu-id="adad5-116">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> <span data-ttu-id="adad5-117">Aby uzyskać więcej informacji, zobacz [porady: MetadataResolver używana do uzyskania powiązanie dynamicznie metadanych](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span><span class="sxs-lookup"><span data-stu-id="adad5-117">For more information, see [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4.  <span data-ttu-id="adad5-118">Generowanie informacji o typie dla każdej umowy.</span><span class="sxs-lookup"><span data-stu-id="adad5-118">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5.  <span data-ttu-id="adad5-119">Teraz można używać tych informacji.</span><span class="sxs-lookup"><span data-stu-id="adad5-119">Now you can use this information.</span></span> <span data-ttu-id="adad5-120">Poniższy przykład umożliwia wygenerowanie kodu źródłowego C#.</span><span class="sxs-lookup"><span data-stu-id="adad5-120">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="adad5-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adad5-121">See Also</span></span>  
 [<span data-ttu-id="adad5-122">Metadane</span><span class="sxs-lookup"><span data-stu-id="adad5-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="adad5-123">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="adad5-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
