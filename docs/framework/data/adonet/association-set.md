---
title: zestaw skojarzeń
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: 43ab6cf9f1ee8cb971810add6b9a89467726f3e2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785030"
---
# <a name="association-set"></a><span data-ttu-id="823a6-102">zestaw skojarzeń</span><span class="sxs-lookup"><span data-stu-id="823a6-102">association set</span></span>
<span data-ttu-id="823a6-103">*Zestaw skojarzeń* to logiczny kontener dla wystąpień [skojarzeń](association-type.md) tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="823a6-103">An *association set* is a logical container for [association](association-type.md) instances of the same type.</span></span> <span data-ttu-id="823a6-104">Zestaw skojarzeń nie jest konstrukcją modelowania danych; oznacza to, że nie opisuje struktury danych lub relacji.</span><span class="sxs-lookup"><span data-stu-id="823a6-104">An association set is not a data modeling construct; that is, it does not describe the structure of data or relationships.</span></span> <span data-ttu-id="823a6-105">Zamiast tego zestaw skojarzeń zawiera konstrukcję dla środowiska hostingu lub magazynu (na przykład środowisko uruchomieniowe języka wspólnego lub SQL Server Database) w celu grupowania wystąpień skojarzeń, aby można je było mapować do magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="823a6-105">Instead, an association set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group association instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="823a6-106">Zestaw skojarzeń jest zdefiniowany w [kontenerze jednostek](entity-container.md), który jest logicznym grupowaniem [zestawów jednostek](entity-set.md) i zestawów skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="823a6-106">An association set is defined within an [entity container](entity-container.md), which is a logical grouping of [entity sets](entity-set.md) and association sets.</span></span>  
  
 <span data-ttu-id="823a6-107">Definicja zestawu skojarzenia zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="823a6-107">A definition for an association set contains the following information:</span></span>  
  
- <span data-ttu-id="823a6-108">Nazwa zestawu skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="823a6-108">The association set name.</span></span> <span data-ttu-id="823a6-109">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="823a6-109">(Required)</span></span>  
  
- <span data-ttu-id="823a6-110">Skojarzenie, którego będzie zawierać wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="823a6-110">The association of which it will contain instances.</span></span> <span data-ttu-id="823a6-111">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="823a6-111">(Required)</span></span>  
  
- <span data-ttu-id="823a6-112">Dwa [punkty końcowe zestawu skojarzenia](association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="823a6-112">Two [association set ends](association-set-end.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="823a6-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="823a6-113">Example</span></span>  
 <span data-ttu-id="823a6-114">Na poniższym diagramie przedstawiono model koncepcyjny z dwoma skojarzeniami: `PublishedBy`i. `WrittenBy`</span><span class="sxs-lookup"><span data-stu-id="823a6-114">The diagram below shows a conceptual model with two associations: `PublishedBy`, and `WrittenBy`.</span></span> <span data-ttu-id="823a6-115">Chociaż informacje o zestawach skojarzeń nie są przekazywane na diagramie, na następnym diagramie przedstawiono przykład zestawów skojarzeń i zestawów jednostek opartych na tym modelu.</span><span class="sxs-lookup"><span data-stu-id="823a6-115">Although information about association sets is not conveyed in the diagram, the next diagram shows an example of association sets and entity sets based on this model.</span></span>  
  
 ![Przykładowy model z trzema typami jednostek](./media/association-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="823a6-117">Poniższy przykład przedstawia zestaw skojarzeń (`PublishedBy`) i dwa zestawy jednostek (`Books` i `Publishers`) na podstawie modelu koncepcyjnego pokazanego powyżej.</span><span class="sxs-lookup"><span data-stu-id="823a6-117">The following example shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="823a6-118">Usługa BI w `Books` zestawie jednostek reprezentuje wystąpienie `Book` typu jednostki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="823a6-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="823a6-119">Podobnie PJ reprezentuje `Publisher` wystąpienie `Publishers` w zestawie jednostek.</span><span class="sxs-lookup"><span data-stu-id="823a6-119">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="823a6-120">BiPj reprezentuje wystąpienie `PublishedBy` skojarzenia `PublishedBy` w zestawie skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="823a6-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Zrzut ekranu pokazujący przykład zestawu.](./media/association-set/sets-example-association.gif)  
  
 <span data-ttu-id="823a6-122">[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="823a6-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="823a6-123">Następujący CSDL definiuje kontener jednostek z jednym zestawem skojarzenia dla każdego skojarzenia na powyższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="823a6-123">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="823a6-124">Należy zauważyć, że nazwa i skojarzenie dla każdego zestawu skojarzeń są zdefiniowane przy użyciu atrybutów XML.</span><span class="sxs-lookup"><span data-stu-id="823a6-124">Note that the name and association for each association set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="823a6-125">Istnieje możliwość zdefiniowania wielu zestawów skojarzeń na każde skojarzenie, o ile żadne z dwóch zestawów skojarzeń nie współdzieli [końca zestawu skojarzenia](association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="823a6-125">It is possible to define multiple association sets per association, as long as no two association sets share an [association set end](association-set-end.md).</span></span> <span data-ttu-id="823a6-126">Poniższy CSDL definiuje kontener jednostek z dwoma zestawami skojarzeń dla `WrittenBy` skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="823a6-126">The following CSDL defines an entity container with two association sets for the `WrittenBy` association.</span></span> <span data-ttu-id="823a6-127">Zauważ, że zdefiniowano wiele zestawów jednostek dla `Book` obiektów i `Author` i że żaden z zestawów skojarzeń nie udostępnia końcowego zestawu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="823a6-127">Notice that multiple entity sets have been defined for the `Book` and `Author` entity types and that no association set shares an association set end.</span></span>  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a><span data-ttu-id="823a6-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="823a6-128">See also</span></span>

- [<span data-ttu-id="823a6-129">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="823a6-129">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="823a6-130">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="823a6-130">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="823a6-131">właściwość klucza obcego</span><span class="sxs-lookup"><span data-stu-id="823a6-131">foreign key property</span></span>](foreign-key-property.md)
