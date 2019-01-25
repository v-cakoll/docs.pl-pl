---
title: Właściwość nawigacji — ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: 6729b22dbc012d5ccfabd64cd83b710833fe1b9d
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857947"
---
# <a name="navigation-property"></a><span data-ttu-id="927a3-102">Właściwość nawigacji</span><span class="sxs-lookup"><span data-stu-id="927a3-102">Navigation property</span></span>

<span data-ttu-id="927a3-103">A *właściwość nawigacji* jest opcjonalną właściwością na [typu jednostki](entity-type.md) umożliwiającą nawigacji z jednego [zakończenia](association-end.md) z [skojarzenia](association-type.md) do Data zakończenia.</span><span class="sxs-lookup"><span data-stu-id="927a3-103">A *navigation property* is an optional property on an [entity type](entity-type.md) that allows for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="927a3-104">W odróżnieniu od innych [właściwości](property.md), właściwości nawigacji nie zawierają danych.</span><span class="sxs-lookup"><span data-stu-id="927a3-104">Unlike other [properties](property.md), navigation properties do not carry data.</span></span>

<span data-ttu-id="927a3-105">Definicja właściwości nawigacji obejmuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="927a3-105">A navigation property definition includes the following:</span></span>

- <span data-ttu-id="927a3-106">Nazwa.</span><span class="sxs-lookup"><span data-stu-id="927a3-106">A name.</span></span> <span data-ttu-id="927a3-107">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="927a3-107">(Required)</span></span>

- <span data-ttu-id="927a3-108">Skojarzenie go przechodzi.</span><span class="sxs-lookup"><span data-stu-id="927a3-108">The association that it navigates.</span></span> <span data-ttu-id="927a3-109">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="927a3-109">(Required)</span></span>

- <span data-ttu-id="927a3-110">Końcach asocjacji, prowadzącego go.</span><span class="sxs-lookup"><span data-stu-id="927a3-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="927a3-111">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="927a3-111">(Required)</span></span>

<span data-ttu-id="927a3-112">Należy pamiętać, że właściwości nawigacji są opcjonalne na obu typów jednostek na końcach asocjacji.</span><span class="sxs-lookup"><span data-stu-id="927a3-112">Note that navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="927a3-113">Jeśli zdefiniujesz właściwości nawigacji na jednym typie jednostek na końcu asocjacji, ma Zdefiniuj właściwość nawigacji typu jednostki na drugim końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="927a3-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>

<span data-ttu-id="927a3-114">Typ danych właściwości nawigacji jest określana przez [liczebność](association-end-multiplicity.md) jego zdalnego [end skojarzenia](association-end.md).</span><span class="sxs-lookup"><span data-stu-id="927a3-114">The data type of a navigation property is determined by the [multiplicity](association-end-multiplicity.md) of its remote [association end](association-end.md).</span></span> <span data-ttu-id="927a3-115">Na przykład, załóżmy, że właściwość nawigacji, `OrdersNavProp`, istnieje na `Customer` typu jednostki i przechodzi skojarzenia typu jeden do wielu między `Customer` i `Order`.</span><span class="sxs-lookup"><span data-stu-id="927a3-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="927a3-116">Ponieważ punkt końcowy skojarzenia zdalnego dla właściwości nawigacji ma liczebność wielu (\*), jego typ danych to kolekcja (z `Order`).</span><span class="sxs-lookup"><span data-stu-id="927a3-116">Because the remote association end for the navigation property has multiplicity of many (\*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="927a3-117">Podobnie, jeśli właściwość nawigacji, `CustomerNavProp`, istnieje na `Order` typu jednostki, będzie jego typu danych `Customer`, ponieważ liczebność drugim końcu jest jeden (1).</span><span class="sxs-lookup"><span data-stu-id="927a3-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>

## <a name="example"></a><span data-ttu-id="927a3-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="927a3-118">Example</span></span>

<span data-ttu-id="927a3-119">Poniższy diagram przedstawia modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`.</span><span class="sxs-lookup"><span data-stu-id="927a3-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="927a3-120">Właściwości nawigacji `Publisher` i `Authors`, są zdefiniowane w typie jednostki książki.</span><span class="sxs-lookup"><span data-stu-id="927a3-120">Navigation properties, `Publisher` and `Authors`, are defined on the Book entity type.</span></span> <span data-ttu-id="927a3-121">Właściwość nawigacji `Books` jest zdefiniowany w obu typ jednostki wydawcy i `Author` typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="927a3-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>

<span data-ttu-id="927a3-122">![Model przy użyciu właściwości nawigacji](/media/modelwithnavprops.gif "ModelWithNavProps")</span><span class="sxs-lookup"><span data-stu-id="927a3-122">![Model with Navigation Properties](/media/modelwithnavprops.gif "ModelWithNavProps")</span></span>

<span data-ttu-id="927a3-123">[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="927a3-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="927a3-124">Definiuje następujące CSDL `Book` typu jednostki, które pokazano na powyższym diagramie:</span><span class="sxs-lookup"><span data-stu-id="927a3-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

<span data-ttu-id="927a3-125">Należy zwrócić uwagę na to, że atrybuty XML są używane do przekazywania informacji niezbędnych do definiowania właściwości nawigacji: Ten atrybut `Name` zawiera nazwę właściwości, `Relationship` zawiera nazwę skojarzenia powoduje przejście, i `FromRole` i `ToRole` zawierają końcach asocjacji.</span><span class="sxs-lookup"><span data-stu-id="927a3-125">Note that XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>

## <a name="see-also"></a><span data-ttu-id="927a3-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="927a3-126">See also</span></span>

- [<span data-ttu-id="927a3-127">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="927a3-127">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="927a3-128">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="927a3-128">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="927a3-129">Relacje, właściwości nawigacji i kluczy obcych</span><span class="sxs-lookup"><span data-stu-id="927a3-129">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
