---
title: Właściwość nawigacji
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: eaf22ad4dd24b4bf046f14ccabd435a9ecd1776f
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094387"
---
# <a name="navigation-property"></a><span data-ttu-id="a0a5b-102">Właściwość nawigacji</span><span class="sxs-lookup"><span data-stu-id="a0a5b-102">Navigation property</span></span>

<span data-ttu-id="a0a5b-103">*Właściwość nawigacji* jest opcjonalną właściwością [typu jednostki](entity-type.md) , która umożliwia nawigację z jednego [końca](association-end.md) [skojarzenia](association-type.md) z drugim.</span><span class="sxs-lookup"><span data-stu-id="a0a5b-103">A *navigation property* is an optional property on an [entity type](entity-type.md) that allows for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="a0a5b-104">W przeciwieństwie do innych [Właściwości](property.md), właściwości nawigacji nie zawierają danych.</span><span class="sxs-lookup"><span data-stu-id="a0a5b-104">Unlike other [properties](property.md), navigation properties do not carry data.</span></span>

<span data-ttu-id="a0a5b-105">Definicja właściwości nawigacji obejmuje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="a0a5b-105">A navigation property definition includes the following:</span></span>

- <span data-ttu-id="a0a5b-106">Nazwa.</span><span class="sxs-lookup"><span data-stu-id="a0a5b-106">A name.</span></span> <span data-ttu-id="a0a5b-107">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="a0a5b-107">(Required)</span></span>

- <span data-ttu-id="a0a5b-108">Skojarzone skojarzenie.</span><span class="sxs-lookup"><span data-stu-id="a0a5b-108">The association that it navigates.</span></span> <span data-ttu-id="a0a5b-109">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="a0a5b-109">(Required)</span></span>

- <span data-ttu-id="a0a5b-110">Koniec skojarzenia, które przechodzi.</span><span class="sxs-lookup"><span data-stu-id="a0a5b-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="a0a5b-111">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="a0a5b-111">(Required)</span></span>

<span data-ttu-id="a0a5b-112">Właściwości nawigacji są opcjonalne na obu typach jednostek na końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="a0a5b-112">Navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="a0a5b-113">Jeśli zdefiniujesz właściwość nawigacji na jednym typie jednostki na końcu skojarzenia, nie musisz definiować właściwości nawigacji dla typu jednostki na drugim końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="a0a5b-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>

<span data-ttu-id="a0a5b-114">Typ danych właściwości nawigacji jest określany przez [liczebność](association-end-multiplicity.md) jego zdalnego [skojarzenia](association-end.md).</span><span class="sxs-lookup"><span data-stu-id="a0a5b-114">The data type of a navigation property is determined by the [multiplicity](association-end-multiplicity.md) of its remote [association end](association-end.md).</span></span> <span data-ttu-id="a0a5b-115">Załóżmy na przykład, że właściwość nawigacji, `OrdersNavProp`, istnieje w typie jednostki `Customer` i przechodzi do skojarzenia jeden-do-wielu między `Customer` i `Order`.</span><span class="sxs-lookup"><span data-stu-id="a0a5b-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="a0a5b-116">Ze względu na to, że zdalne skojarzenie dla właściwości nawigacji ma liczebność wielu (\*), jego typ danych jest kolekcją (`Order`).</span><span class="sxs-lookup"><span data-stu-id="a0a5b-116">Because the remote association end for the navigation property has multiplicity of many (\*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="a0a5b-117">Podobnie, jeśli właściwość nawigacji, `CustomerNavProp`, istnieje w typie jednostki `Order`, jego typ danych będzie `Customer`, ponieważ liczebność elementu zdalnego kończy wynosi jeden (1).</span><span class="sxs-lookup"><span data-stu-id="a0a5b-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>

## <a name="example"></a><span data-ttu-id="a0a5b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0a5b-118">Example</span></span>

<span data-ttu-id="a0a5b-119">Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`.</span><span class="sxs-lookup"><span data-stu-id="a0a5b-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="a0a5b-120">Właściwości nawigacji `Publisher` i `Authors` są zdefiniowane w typie jednostki książki.</span><span class="sxs-lookup"><span data-stu-id="a0a5b-120">The navigation properties `Publisher` and `Authors` are defined on the Book entity type.</span></span> <span data-ttu-id="a0a5b-121">Właściwość nawigacji `Books` jest zdefiniowana zarówno dla typu jednostki wydawcy, jak i typu jednostki `Author`.</span><span class="sxs-lookup"><span data-stu-id="a0a5b-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>

![Diagram przedstawiający model koncepcyjny z trzema typami jednostek.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

<span data-ttu-id="a0a5b-123">[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="a0a5b-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="a0a5b-124">Następujący identyfikator CSDL definiuje typ jednostki `Book` przedstawiony na poniższym diagramie:</span><span class="sxs-lookup"><span data-stu-id="a0a5b-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

<span data-ttu-id="a0a5b-125">Atrybuty XML są używane do przekazywania informacji niezbędnych do zdefiniowania właściwości nawigacji: atrybut `Name` zawiera nazwę właściwości, `Relationship` zawiera nazwę tego skojarzenia, a `FromRole` i `ToRole` zawierają zakończenia skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="a0a5b-125">XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0a5b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0a5b-126">See also</span></span>

- [<span data-ttu-id="a0a5b-127">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="a0a5b-127">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="a0a5b-128">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="a0a5b-128">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="a0a5b-129">Relacje, właściwości nawigacji i klucze obce</span><span class="sxs-lookup"><span data-stu-id="a0a5b-129">Relationships, navigation properties, and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
