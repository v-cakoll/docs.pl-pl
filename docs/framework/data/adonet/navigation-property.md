---
title: "Właściwość nawigacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1677ab1be071eeabd72b29c7ce61d01aaf6164a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="navigation-property"></a><span data-ttu-id="7d288-102">Właściwość nawigacji</span><span class="sxs-lookup"><span data-stu-id="7d288-102">navigation property</span></span>
<span data-ttu-id="7d288-103">A *właściwość nawigacji* jest opcjonalna właściwość na [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) umożliwiająca nawigacji z jednego [zakończenia](../../../../docs/framework/data/adonet/association-end.md) z [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) do Data zakończenia.</span><span class="sxs-lookup"><span data-stu-id="7d288-103">A *navigation property* is an optional property on an [entity type](../../../../docs/framework/data/adonet/entity-type.md) that allows for navigation from one [end](../../../../docs/framework/data/adonet/association-end.md) of an [association](../../../../docs/framework/data/adonet/association-type.md) to the other end.</span></span> <span data-ttu-id="7d288-104">W odróżnieniu od innych [właściwości](../../../../docs/framework/data/adonet/property.md), właściwości nawigacji nie zawierają danych.</span><span class="sxs-lookup"><span data-stu-id="7d288-104">Unlike other [properties](../../../../docs/framework/data/adonet/property.md), navigation properties do not carry data.</span></span>  
  
 <span data-ttu-id="7d288-105">Definicja właściwości nawigacji obejmuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="7d288-105">A navigation property definition includes the following:</span></span>  
  
-   <span data-ttu-id="7d288-106">Nazwa.</span><span class="sxs-lookup"><span data-stu-id="7d288-106">A name.</span></span> <span data-ttu-id="7d288-107">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="7d288-107">(Required)</span></span>  
  
-   <span data-ttu-id="7d288-108">Skojarzenie prowadzącego go.</span><span class="sxs-lookup"><span data-stu-id="7d288-108">The association that it navigates.</span></span> <span data-ttu-id="7d288-109">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="7d288-109">(Required)</span></span>  
  
-   <span data-ttu-id="7d288-110">Punkty końcowe skojarzenia, który nawiguje go.</span><span class="sxs-lookup"><span data-stu-id="7d288-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="7d288-111">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="7d288-111">(Required)</span></span>  
  
 <span data-ttu-id="7d288-112">Należy pamiętać, że właściwości nawigacji są opcjonalne na obu typów jednostek na końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="7d288-112">Note that navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="7d288-113">Definiuje właściwości nawigacji na jeden typ jednostki na końcu skojarzenia, nie trzeba zdefiniować właściwości nawigacji dla typu jednostki na drugim końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="7d288-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>  
  
 <span data-ttu-id="7d288-114">Typ danych właściwości nawigacji jest określany przez [liczebność](../../../../docs/framework/data/adonet/association-end-multiplicity.md) jego zdalnego [końca skojarzenia](../../../../docs/framework/data/adonet/association-end.md).</span><span class="sxs-lookup"><span data-stu-id="7d288-114">The data type of a navigation property is determined by the [multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) of its remote [association end](../../../../docs/framework/data/adonet/association-end.md).</span></span> <span data-ttu-id="7d288-115">Na przykład, załóżmy, że właściwość nawigacji, `OrdersNavProp`, istnieje na `Customer` typu jednostki i przechodzi jeden do wielu skojarzenie `Customer` i `Order`.</span><span class="sxs-lookup"><span data-stu-id="7d288-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="7d288-116">Punkt końcowy zdalnego dla właściwości nawigacji ma liczebność wielu (*), jego typ danych to kolekcja (z `Order`).</span><span class="sxs-lookup"><span data-stu-id="7d288-116">Because the remote association end for the navigation property has multiplicity of many (*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="7d288-117">Podobnie, jeśli właściwość nawigacji, `CustomerNavProp`, istnieje na `Order` typu jednostki, typu danych będzie `Customer`, ponieważ liczebność końca zdalnego jest jeden (1).</span><span class="sxs-lookup"><span data-stu-id="7d288-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d288-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d288-118">Example</span></span>  
 <span data-ttu-id="7d288-119">Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`.</span><span class="sxs-lookup"><span data-stu-id="7d288-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="7d288-120">Właściwości nawigacji `Publisher` i `Authors`, są zdefiniowane w typie jednostek książki.</span><span class="sxs-lookup"><span data-stu-id="7d288-120">Navigation properties, `Publisher` and `Authors`, are defined on the Book entity type.</span></span> <span data-ttu-id="7d288-121">Właściwość nawigacji `Books` jest zdefiniowany w obu typie jednostek wydawcy i `Author` typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="7d288-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>  
  
 <span data-ttu-id="7d288-122">![Modelu z właściwości nawigacji](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")</span><span class="sxs-lookup"><span data-stu-id="7d288-122">![Model with Navigation Properties](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")</span></span>  
  
 <span data-ttu-id="7d288-123">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="7d288-123">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="7d288-124">Definiuje następujące CSDL `Book` typu jednostki pokazano na powyższym diagramie:</span><span class="sxs-lookup"><span data-stu-id="7d288-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="7d288-125">Należy pamiętać, że atrybuty XML są używane do komunikacji informacje niezbędne do definiowania właściwości nawigacji: atrybut `Name` zawiera nazwę właściwości, `Relationship` zawiera nazwę skojarzenia przechodzi on, i `FromRole` i `ToRole` zawierają punkty końcowe skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="7d288-125">Note that XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d288-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d288-126">See Also</span></span>  
 [<span data-ttu-id="7d288-127">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="7d288-127">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="7d288-128">Modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="7d288-128">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
