---
title: Właściwość nawigacji — ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: afb2043abf70fa92ea7cdf8d1e8246d5cdfdba74
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738388"
---
# <a name="navigation-property"></a><span data-ttu-id="f7888-102">Właściwość nawigacji</span><span class="sxs-lookup"><span data-stu-id="f7888-102">Navigation property</span></span>

<span data-ttu-id="f7888-103">*Właściwość nawigacji* jest opcjonalną właściwością [typu jednostki](entity-type.md) , która umożliwia nawigację z jednego [końca](association-end.md) [skojarzenia](association-type.md) z drugim.</span><span class="sxs-lookup"><span data-stu-id="f7888-103">A *navigation property* is an optional property on an [entity type](entity-type.md) that allows for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="f7888-104">W przeciwieństwie do innych [Właściwości](property.md), właściwości nawigacji nie zawierają danych.</span><span class="sxs-lookup"><span data-stu-id="f7888-104">Unlike other [properties](property.md), navigation properties do not carry data.</span></span>

<span data-ttu-id="f7888-105">Definicja właściwości nawigacji obejmuje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="f7888-105">A navigation property definition includes the following:</span></span>

- <span data-ttu-id="f7888-106">Nazwa.</span><span class="sxs-lookup"><span data-stu-id="f7888-106">A name.</span></span> <span data-ttu-id="f7888-107">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="f7888-107">(Required)</span></span>

- <span data-ttu-id="f7888-108">Skojarzone skojarzenie.</span><span class="sxs-lookup"><span data-stu-id="f7888-108">The association that it navigates.</span></span> <span data-ttu-id="f7888-109">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="f7888-109">(Required)</span></span>

- <span data-ttu-id="f7888-110">Koniec skojarzenia, które przechodzi.</span><span class="sxs-lookup"><span data-stu-id="f7888-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="f7888-111">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="f7888-111">(Required)</span></span>

<span data-ttu-id="f7888-112">Należy zauważyć, że właściwości nawigacji są opcjonalne na obu typach jednostek na końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="f7888-112">Note that navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="f7888-113">Jeśli zdefiniujesz właściwość nawigacji na jednym typie jednostki na końcu skojarzenia, nie musisz definiować właściwości nawigacji dla typu jednostki na drugim końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="f7888-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>

<span data-ttu-id="f7888-114">Typ danych właściwości nawigacji jest określany przez [liczebność](association-end-multiplicity.md) jego zdalnego [skojarzenia](association-end.md).</span><span class="sxs-lookup"><span data-stu-id="f7888-114">The data type of a navigation property is determined by the [multiplicity](association-end-multiplicity.md) of its remote [association end](association-end.md).</span></span> <span data-ttu-id="f7888-115">Załóżmy na przykład, że właściwość nawigacji, `OrdersNavProp`, istnieje w typie jednostki `Customer` i przechodzi do skojarzenia jeden-do-wielu między `Customer` i `Order`.</span><span class="sxs-lookup"><span data-stu-id="f7888-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="f7888-116">Ze względu na to, że zdalne skojarzenie dla właściwości nawigacji ma liczebność wielu (\*), jego typ danych jest kolekcją (`Order`).</span><span class="sxs-lookup"><span data-stu-id="f7888-116">Because the remote association end for the navigation property has multiplicity of many (\*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="f7888-117">Podobnie, jeśli właściwość nawigacji, `CustomerNavProp`, istnieje w typie jednostki `Order`, jego typ danych będzie `Customer`, ponieważ liczebność elementu zdalnego kończy wynosi jeden (1).</span><span class="sxs-lookup"><span data-stu-id="f7888-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>

## <a name="example"></a><span data-ttu-id="f7888-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7888-118">Example</span></span>

<span data-ttu-id="f7888-119">Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`.</span><span class="sxs-lookup"><span data-stu-id="f7888-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="f7888-120">Właściwości nawigacji, `Publisher` i `Authors`są zdefiniowane w typie jednostki książki.</span><span class="sxs-lookup"><span data-stu-id="f7888-120">Navigation properties, `Publisher` and `Authors`, are defined on the Book entity type.</span></span> <span data-ttu-id="f7888-121">Właściwość nawigacji `Books` jest zdefiniowana zarówno dla typu jednostki wydawcy, jak i typu jednostki `Author`.</span><span class="sxs-lookup"><span data-stu-id="f7888-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>

 ![Diagram przedstawiający model koncepcyjny z trzema typami jednostek.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

<span data-ttu-id="f7888-123">[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="f7888-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="f7888-124">Następujący identyfikator CSDL definiuje typ jednostki `Book` przedstawiony na poniższym diagramie:</span><span class="sxs-lookup"><span data-stu-id="f7888-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

<span data-ttu-id="f7888-125">Należy zauważyć, że atrybuty XML są używane do przekazywania informacji niezbędnych do zdefiniowania właściwości nawigacji: atrybut `Name` zawiera nazwę właściwości, `Relationship` zawiera nazwę elementu, do którego prowadzi Nawigacja, a `FromRole` i `ToRole` zawierają koniec skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="f7888-125">Note that XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7888-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7888-126">See also</span></span>

- [<span data-ttu-id="f7888-127">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="f7888-127">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="f7888-128">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="f7888-128">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="f7888-129">Relacje, właściwości nawigacji i klucze obce</span><span class="sxs-lookup"><span data-stu-id="f7888-129">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
