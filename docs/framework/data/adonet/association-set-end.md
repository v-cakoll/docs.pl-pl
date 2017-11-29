---
title: Konfigurowanie skojarzenia
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 20810eddda98403d244f6104807504489dde71cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="association-set-end"></a><span data-ttu-id="77c40-102">Konfigurowanie skojarzenia</span><span class="sxs-lookup"><span data-stu-id="77c40-102">association set end</span></span>
<span data-ttu-id="77c40-103">*Konfigurowanie skojarzenia* identyfikuje [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) i [zestaw jednostek](../../../../docs/framework/data/adonet/entity-set.md) na końcu [zestawu skojarzeń](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="77c40-103">An *association set end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) and the [entity set](../../../../docs/framework/data/adonet/entity-set.md) at the end of an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span> <span data-ttu-id="77c40-104">Punkty końcowe skojarzenia zestawu są definiowane jako część zestawu skojarzeń; zestaw skojarzenia musi mieć dokładnie dwa skojarzenie zestawu.</span><span class="sxs-lookup"><span data-stu-id="77c40-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="77c40-105">Koniec definicji zestawu skojarzenia zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="77c40-105">An association set end definition contains the following information:</span></span>  
  
-   <span data-ttu-id="77c40-106">Jeden z typów jednostek objętego skojarzenie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="77c40-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="77c40-107">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="77c40-107">(Required)</span></span>  
  
-   <span data-ttu-id="77c40-108">Zestaw jednostek dla typu jednostki objętego zestawu skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="77c40-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="77c40-109">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="77c40-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="77c40-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="77c40-110">Example</span></span>  
 <span data-ttu-id="77c40-111">Na poniższym diagramie przedstawiono modelu koncepcyjnego z dwóch skojarzenia: `WrittenBy` i `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="77c40-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 <span data-ttu-id="77c40-112">![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="77c40-112">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="77c40-113">Na poniższym diagramie przedstawiono zestawu skojarzeń (`PublishedBy`) i dwa zestawy jednostek (`Books` i `Publishers`) oparte na modelu koncepcyjnego przedstawionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="77c40-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="77c40-114">Skojarzenie zestawu są `Books` i `Publishers` zestawów jednostek.</span><span class="sxs-lookup"><span data-stu-id="77c40-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="77c40-115">Analizy biznesowej w `Books` zestaw jednostek reprezentuje wystąpienie `Book` typu jednostki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="77c40-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="77c40-116">Podobnie, uzyskać reprezentuje `Publisher` wystąpienia w `Publishers` zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="77c40-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="77c40-117">BiPj reprezentuje wystąpienie `PublishedBy` skojarzenia w `PublishedBy` zestawu skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="77c40-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="77c40-118">![Ustawia przykład](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="77c40-118">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="77c40-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa DSL, nazywany języka definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="77c40-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="77c40-120">Następujący plik CSDL definiuje kontenera jednostek z jednego zestawu dla każdego skojarzenia na powyższym diagramie skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="77c40-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="77c40-121">Należy pamiętać, że skojarzenie zestawu są zdefiniowane jako część każdego definicji zestawu skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="77c40-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="77c40-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77c40-122">See Also</span></span>  
 [<span data-ttu-id="77c40-123">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="77c40-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="77c40-124">Modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="77c40-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
