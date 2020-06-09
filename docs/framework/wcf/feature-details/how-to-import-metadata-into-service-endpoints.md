---
title: 'Instrukcje: Importowanie metadanych do punktów końcowych usług'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: 1de316b8e91739d5e3e24ff960e2cdfb33cc7fab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597062"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="69c96-102">Instrukcje: Importowanie metadanych do punktów końcowych usług</span><span class="sxs-lookup"><span data-stu-id="69c96-102">How to: Import Metadata into Service Endpoints</span></span>
<span data-ttu-id="69c96-103">W tym temacie opisano sposób importowania metadanych do kolekcji punktów końcowych usługi i używania usługi zdefiniowanej w [wprowadzenie](../samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="69c96-103">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../samples/getting-started-sample.md).</span></span> <span data-ttu-id="69c96-104">W tym temacie pokazano, jak utworzyć aplikację kliencką, która importuje metadane z usługi, a następnie wywołuje `Add` metodę w usłudze.</span><span class="sxs-lookup"><span data-stu-id="69c96-104">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="69c96-105">Aby zaimportować metadane do punktów końcowych usługi</span><span class="sxs-lookup"><span data-stu-id="69c96-105">To import metadata into service endpoints</span></span>  
  
1. <span data-ttu-id="69c96-106">Zadeklaruj <xref:System.ServiceModel.EndpointAddress> obiekt i zainicjuj go za pomocą Uniform Resource Identifier (URI) dla adresu wymiany metadanych (Mex) usługi.</span><span class="sxs-lookup"><span data-stu-id="69c96-106">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. <span data-ttu-id="69c96-107">Utwórz <xref:System.ServiceModel.Description.MetadataExchangeClient> , przekazując w adresie MEX i Wywołaj <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> .</span><span class="sxs-lookup"><span data-stu-id="69c96-107">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="69c96-108">Spowoduje to pobranie metadanych z usługi.</span><span class="sxs-lookup"><span data-stu-id="69c96-108">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. <span data-ttu-id="69c96-109">Utwórz <xref:System.ServiceModel.Description.WsdlImporter> , przekazując do metadanych wcześniej pobrane i Wywołaj <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> .</span><span class="sxs-lookup"><span data-stu-id="69c96-109">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="69c96-110">Spowoduje to wygenerowanie kolekcji <xref:System.ServiceModel.Description.ContractDescription> obiektów.</span><span class="sxs-lookup"><span data-stu-id="69c96-110">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="69c96-111">Możesz również wywołać <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> lub <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A> , w zależności od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="69c96-111">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="69c96-112">Po zaimportowaniu metadanych nie będzie można utworzyć kanału klienta lub wyeksportować metadanych.</span><span class="sxs-lookup"><span data-stu-id="69c96-112">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="69c96-113">Dzieje się tak, ponieważ w tym punkcie nie są dostępne żadne informacje o typie.</span><span class="sxs-lookup"><span data-stu-id="69c96-113">This is because no type information is available at this point.</span></span> <span data-ttu-id="69c96-114">Informacje o typie są wymagane do rzeczywistego współdziałania z usługą lub do eksportowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="69c96-114">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="69c96-115">Aby wygenerować informacje o typie, należy wygenerować kod, przedstawiony w krokach 4 i 5.</span><span class="sxs-lookup"><span data-stu-id="69c96-115">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="69c96-116">Alternatywnie można użyć <xref:System.ServiceModel.Description.MetadataResolver> klasy pomocnika.</span><span class="sxs-lookup"><span data-stu-id="69c96-116">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> <span data-ttu-id="69c96-117">Aby uzyskać więcej informacji, zobacz [How to: use klasy MetadataResolver do dynamicznego uzyskiwania metadanych powiązania](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span><span class="sxs-lookup"><span data-stu-id="69c96-117">For more information, see [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4. <span data-ttu-id="69c96-118">Generuj informacje o typie dla każdego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="69c96-118">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. <span data-ttu-id="69c96-119">Teraz możesz użyć tych informacji.</span><span class="sxs-lookup"><span data-stu-id="69c96-119">Now you can use this information.</span></span> <span data-ttu-id="69c96-120">Poniższy przykład generuje kod źródłowy języka C#.</span><span class="sxs-lookup"><span data-stu-id="69c96-120">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="69c96-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69c96-121">See also</span></span>

- [<span data-ttu-id="69c96-122">Metadane</span><span class="sxs-lookup"><span data-stu-id="69c96-122">Metadata</span></span>](metadata.md)
- [<span data-ttu-id="69c96-123">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="69c96-123">Getting Started</span></span>](../samples/getting-started-sample.md)
