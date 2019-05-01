---
title: 'Instrukcje: importowanie metadanych do punktów końcowych usług'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: afee3f2236db99b14c0e840d987e4862a260568e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047831"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="a5827-102">Instrukcje: importowanie metadanych do punktów końcowych usług</span><span class="sxs-lookup"><span data-stu-id="a5827-102">How to: Import Metadata into Service Endpoints</span></span>
<span data-ttu-id="a5827-103">W tym temacie wyjaśniono, jak zaimportować metadane do kolekcji punktów końcowych usługi i korzystać z niej zdefiniowane w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a5827-103">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="a5827-104">W tym temacie pokazano, jak utworzyć aplikację kliencką, która importuje metadane z usługi, a następnie wywołania `Add` metody dla usługi.</span><span class="sxs-lookup"><span data-stu-id="a5827-104">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="a5827-105">Aby zaimportować metadane do punktów końcowych usług</span><span class="sxs-lookup"><span data-stu-id="a5827-105">To import metadata into service endpoints</span></span>  
  
1. <span data-ttu-id="a5827-106">Zadeklaruj <xref:System.ServiceModel.EndpointAddress> obiektu i go zainicjować za pomocą identyfikatora URI (Uniform Resource) dla adresu programu exchange (MEX) metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="a5827-106">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. <span data-ttu-id="a5827-107">Tworzenie <xref:System.ServiceModel.Description.MetadataExchangeClient>, przekazując MEX adresa i Wywołaj <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5827-107">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="a5827-108">To pobiera metadane z usługi.</span><span class="sxs-lookup"><span data-stu-id="a5827-108">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. <span data-ttu-id="a5827-109">Tworzenie <xref:System.ServiceModel.Description.WsdlImporter>, przekazując metadanych wcześniej pobrane i Wywołaj <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5827-109">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="a5827-110">Spowoduje to wygenerowanie zbiór <xref:System.ServiceModel.Description.ContractDescription> obiektów.</span><span class="sxs-lookup"><span data-stu-id="a5827-110">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="a5827-111">Można również wywołać <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> lub <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, w zależności od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="a5827-111">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    >  <span data-ttu-id="a5827-112">Po zaimportowaniu metadanych nie można utworzyć kanału klienta lub wyeksportować metadane.</span><span class="sxs-lookup"><span data-stu-id="a5827-112">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="a5827-113">Jest to spowodowane typu są dostępne żadne informacje w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="a5827-113">This is because no type information is available at this point.</span></span> <span data-ttu-id="a5827-114">Informacje o typie jest wymagany do faktycznie wchodzić w interakcje z usługą lub eksportowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="a5827-114">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="a5827-115">Aby wygenerować informacje o typie, należy wygenerować kod, przedstawiono w ramach kroków 4 i 5.</span><span class="sxs-lookup"><span data-stu-id="a5827-115">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="a5827-116">Alternatywnie można użyć <xref:System.ServiceModel.Description.MetadataResolver> Klasa pomocy.</span><span class="sxs-lookup"><span data-stu-id="a5827-116">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> <span data-ttu-id="a5827-117">Aby uzyskać więcej informacji, zobacz [jak: Uzyskiwanie metadanych powiązania przy użyciu klasy MetadataResolver](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span><span class="sxs-lookup"><span data-stu-id="a5827-117">For more information, see [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4. <span data-ttu-id="a5827-118">Generuj informacje o typie dla każdej umowy.</span><span class="sxs-lookup"><span data-stu-id="a5827-118">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. <span data-ttu-id="a5827-119">Teraz można użyć tych informacji.</span><span class="sxs-lookup"><span data-stu-id="a5827-119">Now you can use this information.</span></span> <span data-ttu-id="a5827-120">Poniższy przykład spowoduje wygenerowanie C# kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="a5827-120">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a5827-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5827-121">See also</span></span>

- [<span data-ttu-id="a5827-122">Metadane</span><span class="sxs-lookup"><span data-stu-id="a5827-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="a5827-123">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="a5827-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
