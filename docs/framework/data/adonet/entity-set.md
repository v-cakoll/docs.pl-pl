---
title: Zestaw jednostek
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 050c73d3fd9146c8eee83baf1bd504acc18c8718
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="entity-set"></a><span data-ttu-id="f656d-102">Zestaw jednostek</span><span class="sxs-lookup"><span data-stu-id="f656d-102">entity set</span></span>
<span data-ttu-id="f656d-103">*Zestaw jednostek* jest kontenerem logicznym dla wystąpień [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) i wystąpień dowolnego typu pochodzącego od tego typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="f656d-103">An *entity set* is a logical container for instances of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) and instances of any type derived from that entity type.</span></span> <span data-ttu-id="f656d-104">(Informacje o typach pochodnych, zobacz [modelu Entity Data Model: dziedziczenie](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) Relacja między typem obiektu a zestaw jednostek jest odpowiednikiem relację wiersz tabeli relacyjnej bazy danych: jak wiersz, typem jednostki opisuje struktura danych i, jak tabelę, zestaw jednostek zawiera wystąpień danego struktury.</span><span class="sxs-lookup"><span data-stu-id="f656d-104">(For information about derived types, see [Entity Data Model: Inheritance](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) The relationship between an entity type and an entity set is analogous to the relationship between a row and a table in a relational database: Like a row, an entity type describes data structure, and, like a table, an entity set contains instances of a given structure.</span></span> <span data-ttu-id="f656d-105">Zestaw jednostek nie jest danych modelowania konstrukcji; nie opisano w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="f656d-105">An entity set is not a data modeling construct; it does not describe the structure of data.</span></span> <span data-ttu-id="f656d-106">Zamiast tego zestawu jednostek zapewnia konstrukcję w środowisku obsługującym lub magazynu (na przykład środowisko uruchomieniowe języka wspólnego lub bazy danych programu SQL Server) do wystąpień typów jednostek grupy mogą być mapowane do magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="f656d-106">Instead, an entity set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group entity type instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="f656d-107">Zestaw jednostek jest zdefiniowany w [kontenera jednostek](../../../../docs/framework/data/adonet/entity-container.md), która jest logiczne grupowanie zestawów jednostek i [ustawia skojarzenie](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="f656d-107">An entity set is defined within an [entity container](../../../../docs/framework/data/adonet/entity-container.md), which is a logical grouping of entity sets and [association sets](../../../../docs/framework/data/adonet/association-set.md).</span></span>  
  
 <span data-ttu-id="f656d-108">W przypadku wystąpienia typu jednostki istnieje w zestawie jednostek musi spełnienia następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="f656d-108">For an entity type instance to exist in an entity set, the following must be true:</span></span>  
  
-   <span data-ttu-id="f656d-109">Typ wystąpienia jest ona taka sama jak typ jednostki, na którym jest oparty ten zestaw jednostek lub typ wystąpienia jest podtypem typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="f656d-109">The type of the instance is either the same as the entity type on which the entity set is based, or the type of the instance is a subtype of the entity type.</span></span>  
  
-   <span data-ttu-id="f656d-110">[Klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) wystąpienie jest unikatowa w obrębie zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="f656d-110">The [entity key](../../../../docs/framework/data/adonet/entity-key.md) for the instance is unique within the entity set.</span></span>  
  
-   <span data-ttu-id="f656d-111">Wystąpienie nie istnieje w innym zestawie jednostek.</span><span class="sxs-lookup"><span data-stu-id="f656d-111">The instance does not exist in any other entity set.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f656d-112">Wiele zestawów jednostek można zdefiniować przy użyciu tego samego typu jednostki, ale wystąpienie typu danej jednostki może istnieć tylko w zestawie jedną jednostkę.</span><span class="sxs-lookup"><span data-stu-id="f656d-112">Multiple entity sets can be defined using the same entity type, but an instance of a given entity type can only exist in one entity set.</span></span>  
  
 <span data-ttu-id="f656d-113">Nie trzeba zdefiniować zestaw jednostek dla poszczególnych typów jednostek w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="f656d-113">You do not have to define an entity set for each entity type in a conceptual model.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f656d-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="f656d-114">Example</span></span>  
 <span data-ttu-id="f656d-115">Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`.</span><span class="sxs-lookup"><span data-stu-id="f656d-115">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 <span data-ttu-id="f656d-116">![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="f656d-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="f656d-117">Na poniższym diagramie przedstawiono dwa zestawy jednostek (`Books` i `Publishers`) i zestaw skojarzeń (`PublishedBy`) oparte na modelu koncepcyjnego przedstawionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="f656d-117">The following diagram shows two entity sets (`Books` and `Publishers`) and an association set (`PublishedBy`) based on the conceptual model shown above.</span></span> <span data-ttu-id="f656d-118">Analizy biznesowej w `Books` zestaw jednostek reprezentuje wystąpienie `Book` typu jednostki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f656d-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="f656d-119">Podobnie, uzyskać reprezentują `Publisher` wystąpienia w `Publishers` zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="f656d-119">Similarly, Pj represent a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="f656d-120">BiPj reprezentuje wystąpienie `PublishedBy` skojarzenia w `PublishedBy` zestawu skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="f656d-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="f656d-121">![Ustawia przykład](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="f656d-121">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="f656d-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="f656d-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="f656d-123">Następujący plik CSDL definiuje kontenera jednostek o jeden zestaw jednostek dla poszczególnych typów jednostek w modelu koncepcyjnym przedstawionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="f656d-123">The following CSDL defines an entity container with one entity set for each entity type in the conceptual model shown above.</span></span> <span data-ttu-id="f656d-124">Należy pamiętać, że typ nazwy i jednostki dla każdego zestawu jednostek są zdefiniowane przy użyciu atrybutów XML.</span><span class="sxs-lookup"><span data-stu-id="f656d-124">Note that the name and entity type for each entity set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="f656d-125">Istnieje możliwość definiowania wielu zestawów jednostek na typ (MEST).</span><span class="sxs-lookup"><span data-stu-id="f656d-125">It is possible to define multiple entity sets per type (MEST).</span></span> <span data-ttu-id="f656d-126">Następujący plik CSDL definiuje kontenera jednostek z dwóch zestawów jednostek dla `Book` typ jednostki:</span><span class="sxs-lookup"><span data-stu-id="f656d-126">The following CSDL defines an entity container with two entity sets for the `Book` entity type:</span></span>  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a><span data-ttu-id="f656d-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f656d-127">See Also</span></span>  
 [<span data-ttu-id="f656d-128">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="f656d-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="f656d-129">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="f656d-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
