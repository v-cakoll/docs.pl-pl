---
title: "zestawu skojarzeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: db293cbc636d0ae4e532f24b2852444395f603c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="association-set"></a><span data-ttu-id="813fc-102">zestawu skojarzeń</span><span class="sxs-lookup"><span data-stu-id="813fc-102">association set</span></span>
<span data-ttu-id="813fc-103">*Zestawu skojarzeń* jest kontenerem logicznym dla [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) wystąpień tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="813fc-103">An *association set* is a logical container for [association](../../../../docs/framework/data/adonet/association-type.md) instances of the same type.</span></span> <span data-ttu-id="813fc-104">Zestaw skojarzenia nie jest danych modelowania konstrukcji; oznacza to, że nie opisano struktury danych lub relacji.</span><span class="sxs-lookup"><span data-stu-id="813fc-104">An association set is not a data modeling construct; that is, it does not describe the structure of data or relationships.</span></span> <span data-ttu-id="813fc-105">Zamiast tego zestawu skojarzeń zapewnia konstrukcję w środowisku obsługującym lub magazynu (na przykład środowisko uruchomieniowe języka wspólnego lub bazy danych programu SQL Server) do wystąpień skojarzenie grupy mogą być mapowane do magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="813fc-105">Instead, an association set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group association instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="813fc-106">Zestaw skojarzenia są zdefiniowane w obrębie [kontenera jednostek](../../../../docs/framework/data/adonet/entity-container.md), która jest logiczną grupę [zestawów jednostek](../../../../docs/framework/data/adonet/entity-set.md) i zestawy skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="813fc-106">An association set is defined within an [entity container](../../../../docs/framework/data/adonet/entity-container.md), which is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md) and association sets.</span></span>  
  
 <span data-ttu-id="813fc-107">Definicja zestawu skojarzeń zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="813fc-107">A definition for an association set contains the following information:</span></span>  
  
-   <span data-ttu-id="813fc-108">Nazwa zestawu skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="813fc-108">The association set name.</span></span> <span data-ttu-id="813fc-109">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="813fc-109">(Required)</span></span>  
  
-   <span data-ttu-id="813fc-110">Skojarzenia, z których będzie zawierać wystąpień.</span><span class="sxs-lookup"><span data-stu-id="813fc-110">The association of which it will contain instances.</span></span> <span data-ttu-id="813fc-111">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="813fc-111">(Required)</span></span>  
  
-   <span data-ttu-id="813fc-112">Dwa [skojarzenia ustawić kończy się](../../../../docs/framework/data/adonet/association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="813fc-112">Two [association set ends](../../../../docs/framework/data/adonet/association-set-end.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="813fc-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="813fc-113">Example</span></span>  
 <span data-ttu-id="813fc-114">Na poniższym diagramie przedstawiono modelu koncepcyjnego z dwóch skojarzenia: `PublishedBy`, i `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="813fc-114">The diagram below shows a conceptual model with two associations: `PublishedBy`, and `WrittenBy`.</span></span> <span data-ttu-id="813fc-115">Chociaż informacje o zestawach skojarzenia nie jest przekazywany w schemacie, diagram dalej przedstawiono przykład skojarzenia zestawów i zestawów jednostek na podstawie tego modelu.</span><span class="sxs-lookup"><span data-stu-id="813fc-115">Although information about association sets is not conveyed in the diagram, the next diagram shows an example of association sets and entity sets based on this model.</span></span>  
  
 <span data-ttu-id="813fc-116">![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="813fc-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="813fc-117">W poniższym przykładzie przedstawiono zestawu skojarzeń (`PublishedBy`) i dwa zestawy jednostek (`Books` i `Publishers`) oparte na modelu koncepcyjnego przedstawionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="813fc-117">The following example shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="813fc-118">Analizy biznesowej w `Books` zestaw jednostek reprezentuje wystąpienie `Book` typu jednostki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="813fc-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="813fc-119">Podobnie, uzyskać reprezentuje `Publisher` wystąpienia w `Publishers` zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="813fc-119">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="813fc-120">BiPj reprezentuje wystąpienie `PublishedBy` skojarzenia w `PublishedBy` zestawu skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="813fc-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="813fc-121">![Ustawia przykład](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="813fc-121">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="813fc-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="813fc-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="813fc-123">Następujący plik CSDL definiuje kontenera jednostek z jednego zestawu dla każdego skojarzenia na powyższym diagramie skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="813fc-123">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="813fc-124">Należy pamiętać, że nazwa i skojarzenia dla każdego skojarzenia są zdefiniowane przy użyciu atrybutów XML.</span><span class="sxs-lookup"><span data-stu-id="813fc-124">Note that the name and association for each association set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="813fc-125">Można zdefiniować wiele zestawów skojarzenie na skojarzenie tak długo, jak nie skojarzenie dwóch zestawów udziału [Konfigurowanie skojarzenia](../../../../docs/framework/data/adonet/association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="813fc-125">It is possible to define multiple association sets per association, as long as no two association sets share an [association set end](../../../../docs/framework/data/adonet/association-set-end.md).</span></span> <span data-ttu-id="813fc-126">Następujący plik CSDL definiuje kontenera jednostek z dwoma zestawami skojarzenia dla `WrittenBy` skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="813fc-126">The following CSDL defines an entity container with two association sets for the `WrittenBy` association.</span></span> <span data-ttu-id="813fc-127">Należy zauważyć, że wiele zestawów jednostek zostały zdefiniowane dla `Book` i `Author` Konfigurowanie typów jednostek i że żaden związek ustawić udziały skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="813fc-127">Notice that multiple entity sets have been defined for the `Book` and `Author` entity types and that no association set shares an association set end.</span></span>  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a><span data-ttu-id="813fc-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="813fc-128">See Also</span></span>  
 [<span data-ttu-id="813fc-129">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="813fc-129">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="813fc-130">Modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="813fc-130">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="813fc-131">Właściwość klucza obcego</span><span class="sxs-lookup"><span data-stu-id="813fc-131">foreign key property</span></span>](../../../../docs/framework/data/adonet/foreign-key-property.md)
