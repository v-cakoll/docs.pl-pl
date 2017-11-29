---
title: Kontenera jednostek
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5ac4383e68aad49af1a65988d9993f6fa018b31a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="entity-container"></a><span data-ttu-id="97a23-102">Kontenera jednostek</span><span class="sxs-lookup"><span data-stu-id="97a23-102">entity container</span></span>
<span data-ttu-id="97a23-103">*Kontenera jednostek* to logiczne grupowanie [zestawów jednostek](../../../../docs/framework/data/adonet/entity-set.md), [ustawia skojarzenie](../../../../docs/framework/data/adonet/association-set.md), i [importów funkcji](../../../../docs/framework/data/adonet/model-declared-function.md).</span><span class="sxs-lookup"><span data-stu-id="97a23-103">An *entity container* is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md), [association sets](../../../../docs/framework/data/adonet/association-set.md), and [function imports](../../../../docs/framework/data/adonet/model-declared-function.md).</span></span>  
  
 <span data-ttu-id="97a23-104">Wymaga spełnienia następujących warunków kontenera jednostek zdefiniowanych w modelu koncepcyjnym:</span><span class="sxs-lookup"><span data-stu-id="97a23-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
-   <span data-ttu-id="97a23-105">Co najmniej jedną jednostkę kontenera musi być zdefiniowana w każdym modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="97a23-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
-   <span data-ttu-id="97a23-106">Kontenera jednostek musi mieć unikatową nazwę w ramach każdego modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="97a23-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="97a23-107">Kontenera jednostek można zdefiniować zestawy jednostek lub zestawy skojarzenia, używające typy jednostek i skojarzenia zdefiniowane w jedną lub kilka przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="97a23-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="97a23-108">Aby uzyskać więcej informacji, zobacz [modelu Entity Data Model: przestrzenie nazw](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="97a23-108">For more information, see [Entity Data Model: Namespaces](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="97a23-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="97a23-109">Example</span></span>  
 <span data-ttu-id="97a23-110">Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`.</span><span class="sxs-lookup"><span data-stu-id="97a23-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="97a23-111">Zapoznaj się z przykładem dalej, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="97a23-111">See the next example for more information.</span></span>  
  
 <span data-ttu-id="97a23-112">![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="97a23-112">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="97a23-113">Mimo że diagram nie mogą służyć do przekazywania informacji kontenera jednostek, modelu koncepcyjnego musi definiować kontenera jednostek.</span><span class="sxs-lookup"><span data-stu-id="97a23-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="97a23-114">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa DSL, nazywany języka definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="97a23-114">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="97a23-115">Następujący plik CSDL definiuje kontenera jednostek dla modelu koncepcyjnego pokazano na powyższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="97a23-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="97a23-116">Należy pamiętać, że nazwa kontenera jednostek jest zdefiniowany w atrybutu XML.</span><span class="sxs-lookup"><span data-stu-id="97a23-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="97a23-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97a23-117">See Also</span></span>  
 [<span data-ttu-id="97a23-118">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="97a23-118">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="97a23-119">Modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="97a23-119">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
