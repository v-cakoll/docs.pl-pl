---
title: punkt końcowy zestawu skojarzeń
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 48ba84d46e380462405551cc2d826d84368b351a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786932"
---
# <a name="association-set-end"></a><span data-ttu-id="fd7ca-102">punkt końcowy zestawu skojarzeń</span><span class="sxs-lookup"><span data-stu-id="fd7ca-102">association set end</span></span>
<span data-ttu-id="fd7ca-103">*Koniec zestawu skojarzeń* identyfikuje [Typ jednostki](entity-type.md) i [jednostkę ustawioną](entity-set.md) na końcu [zestawu skojarzenia](association-set.md).</span><span class="sxs-lookup"><span data-stu-id="fd7ca-103">An *association set end* identifies the [entity type](entity-type.md) and the [entity set](entity-set.md) at the end of an [association set](association-set.md).</span></span> <span data-ttu-id="fd7ca-104">Zakończenia zestawu skojarzeń są definiowane jako część zestawu skojarzenia; zestaw skojarzeń musi mieć dokładnie dwa punkty końcowe zestawu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="fd7ca-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="fd7ca-105">Definicja końcowa zestawu skojarzeń zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="fd7ca-105">An association set end definition contains the following information:</span></span>  
  
- <span data-ttu-id="fd7ca-106">Jeden z typów jednostek należących do zestawu skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="fd7ca-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="fd7ca-107">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="fd7ca-107">(Required)</span></span>  
  
- <span data-ttu-id="fd7ca-108">Zestaw jednostek dla typu jednostki, który jest powiązany z zestawem skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="fd7ca-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="fd7ca-109">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="fd7ca-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd7ca-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd7ca-110">Example</span></span>  
 <span data-ttu-id="fd7ca-111">Na poniższym diagramie przedstawiono model koncepcyjny z dwoma skojarzeniami: `WrittenBy` i `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="fd7ca-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![Przykładowy model z trzema typami jednostek](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="fd7ca-113">Na poniższym diagramie przedstawiono zestaw skojarzeń (`PublishedBy`) i dwa zestawy jednostek (`Books` i `Publishers`) na podstawie modelu koncepcyjnego pokazanego powyżej.</span><span class="sxs-lookup"><span data-stu-id="fd7ca-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="fd7ca-114">Zestaw skojarzeń zostaje zakończony `Books` i `Publishers` zestawy jednostek.</span><span class="sxs-lookup"><span data-stu-id="fd7ca-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="fd7ca-115">Usługa BI w `Books` zestawie jednostek reprezentuje wystąpienie `Book` typu jednostki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fd7ca-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="fd7ca-116">Podobnie PJ reprezentuje `Publisher` wystąpienie `Publishers` w zestawie jednostek.</span><span class="sxs-lookup"><span data-stu-id="fd7ca-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="fd7ca-117">BiPj reprezentuje wystąpienie `PublishedBy` skojarzenia `PublishedBy` w zestawie skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="fd7ca-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Zrzut ekranu pokazujący przykład zestawu.](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="fd7ca-119">[ADO.NET Entity Framework](./ef/index.md) używa języka DSL o nazwie koncepcyjny schemat definicji schematu ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="fd7ca-119">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="fd7ca-120">Następujący CSDL definiuje kontener jednostek z jednym zestawem skojarzenia dla każdego skojarzenia na powyższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="fd7ca-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="fd7ca-121">Należy zauważyć, że końcówki zestawu skojarzeń są zdefiniowane jako część każdej definicji zestawu skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="fd7ca-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="fd7ca-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd7ca-122">See also</span></span>

- [<span data-ttu-id="fd7ca-123">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="fd7ca-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="fd7ca-124">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="fd7ca-124">Entity Data Model</span></span>](entity-data-model.md)
