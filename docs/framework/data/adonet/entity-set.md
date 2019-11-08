---
title: zestaw jednostek
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 5a2465801c270813dd7bca2144d05fa202571153
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738422"
---
# <a name="entity-set"></a><span data-ttu-id="1f9ec-102">zestaw jednostek</span><span class="sxs-lookup"><span data-stu-id="1f9ec-102">entity set</span></span>
<span data-ttu-id="1f9ec-103">*Zestaw jednostek* to logiczny kontener dla wystąpień [typu jednostki](entity-type.md) i wystąpień dowolnego typu pochodzącego od tego typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-103">An *entity set* is a logical container for instances of an [entity type](entity-type.md) and instances of any type derived from that entity type.</span></span> <span data-ttu-id="1f9ec-104">(Aby uzyskać informacje o typach pochodnych, zobacz [Entity Data Model: dziedziczenie](entity-data-model-inheritance.md)). Relacja między typem jednostki a zestawem jednostek jest analogiczna do relacji między wierszem a tabelą w relacyjnej bazie danych: podobnie jak w przypadku wiersza, typ jednostki opisuje strukturę danych i, podobnie jak tabela, zestaw jednostek zawiera wystąpienia danej struktury.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-104">(For information about derived types, see [Entity Data Model: Inheritance](entity-data-model-inheritance.md).) The relationship between an entity type and an entity set is analogous to the relationship between a row and a table in a relational database: Like a row, an entity type describes data structure, and, like a table, an entity set contains instances of a given structure.</span></span> <span data-ttu-id="1f9ec-105">Zestaw jednostek nie jest konstrukcją modelowania danych; nie opisuje struktury danych.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-105">An entity set is not a data modeling construct; it does not describe the structure of data.</span></span> <span data-ttu-id="1f9ec-106">Zamiast tego zestaw jednostek zapewnia konstrukcję dla środowiska hostingu lub magazynu (na przykład środowisko uruchomieniowe języka wspólnego lub SQL Server Database) do grupowania wystąpień typu jednostki, dzięki czemu można je mapować do magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-106">Instead, an entity set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group entity type instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="1f9ec-107">Zestaw jednostek jest zdefiniowany w [kontenerze jednostek](entity-container.md), który jest logicznym grupowaniem zestawów jednostek i [zestawów skojarzeń](association-set.md).</span><span class="sxs-lookup"><span data-stu-id="1f9ec-107">An entity set is defined within an [entity container](entity-container.md), which is a logical grouping of entity sets and [association sets](association-set.md).</span></span>  
  
 <span data-ttu-id="1f9ec-108">W przypadku wystąpienia typu jednostki, które ma istnieć w zestawie jednostek, muszą być spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="1f9ec-108">For an entity type instance to exist in an entity set, the following must be true:</span></span>  
  
- <span data-ttu-id="1f9ec-109">Typ wystąpienia jest taki sam jak typ jednostki, na której bazuje zestaw jednostek lub typ wystąpienia jest podtypem typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-109">The type of the instance is either the same as the entity type on which the entity set is based, or the type of the instance is a subtype of the entity type.</span></span>  
  
- <span data-ttu-id="1f9ec-110">[Klucz jednostki](entity-key.md) dla wystąpienia jest unikatowy w ramach zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-110">The [entity key](entity-key.md) for the instance is unique within the entity set.</span></span>  
  
- <span data-ttu-id="1f9ec-111">Wystąpienie nie istnieje w żadnym innym zestawie jednostek.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-111">The instance does not exist in any other entity set.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1f9ec-112">Wiele zestawów jednostek można zdefiniować przy użyciu tego samego typu jednostki, ale wystąpienie danego typu jednostki może istnieć tylko w jednym zestawie jednostek.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-112">Multiple entity sets can be defined using the same entity type, but an instance of a given entity type can only exist in one entity set.</span></span>  
  
 <span data-ttu-id="1f9ec-113">Nie trzeba definiować zestawu jednostek dla każdego typu jednostki w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-113">You do not have to define an entity set for each entity type in a conceptual model.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f9ec-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f9ec-114">Example</span></span>  
 <span data-ttu-id="1f9ec-115">Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-115">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Przykładowy model z trzema typami jednostek](./media/entity-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="1f9ec-117">Na poniższym diagramie przedstawiono dwa zestawy jednostek (`Books` i `Publishers`) oraz zestaw skojarzeń (`PublishedBy`) na podstawie modelu koncepcyjnego pokazanego powyżej.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-117">The following diagram shows two entity sets (`Books` and `Publishers`) and an association set (`PublishedBy`) based on the conceptual model shown above.</span></span> <span data-ttu-id="1f9ec-118">Usługa BI w zestawie jednostek `Books` reprezentuje wystąpienie typu jednostki `Book` w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="1f9ec-119">Podobnie PJ reprezentuje wystąpienie `Publisher` w zestawie jednostek `Publishers`.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-119">Similarly, Pj represent a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="1f9ec-120">BiPj reprezentuje wystąpienie skojarzenia `PublishedBy` w zestawie skojarzeń `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Zrzut ekranu pokazujący przykład zestawu.](./media/entity-set/sets-example-association.gif)  
  
 <span data-ttu-id="1f9ec-122">[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="1f9ec-123">Poniższy identyfikator CSDL definiuje kontener jednostek z jednym zestawem jednostek dla każdego typu jednostki w modelu koncepcyjnym pokazanym powyżej.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-123">The following CSDL defines an entity container with one entity set for each entity type in the conceptual model shown above.</span></span> <span data-ttu-id="1f9ec-124">Należy zauważyć, że nazwa i typ jednostki dla każdego zestawu jednostek są zdefiniowane przy użyciu atrybutów XML.</span><span class="sxs-lookup"><span data-stu-id="1f9ec-124">Note that the name and entity type for each entity set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="1f9ec-125">Istnieje możliwość zdefiniowania wielu zestawów jednostek na typ (MEST).</span><span class="sxs-lookup"><span data-stu-id="1f9ec-125">It is possible to define multiple entity sets per type (MEST).</span></span> <span data-ttu-id="1f9ec-126">Następujący CSDL definiuje kontener jednostek z dwoma zestawami jednostek dla `Book` typ jednostki:</span><span class="sxs-lookup"><span data-stu-id="1f9ec-126">The following CSDL defines an entity container with two entity sets for the `Book` entity type:</span></span>  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a><span data-ttu-id="1f9ec-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f9ec-127">See also</span></span>

- [<span data-ttu-id="1f9ec-128">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="1f9ec-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="1f9ec-129">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="1f9ec-129">Entity Data Model</span></span>](entity-data-model.md)
