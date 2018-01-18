---
title: "punkt końcowy skojarzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ffa768f50b3a80c22b4c84cffaf42897193a7d9f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="association-end"></a><span data-ttu-id="1d18a-102">punkt końcowy skojarzenia</span><span class="sxs-lookup"><span data-stu-id="1d18a-102">association end</span></span>
<span data-ttu-id="1d18a-103">*Końca skojarzenia* identyfikuje [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) na jeden z końców [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) i liczby jednostek wpisz wystąpień, które mogą znajdować się na tym końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="1d18a-103">An *association end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) on one end of an [association](../../../../docs/framework/data/adonet/association-type.md) and the number of entity type instances that can exist at that end of an association.</span></span> <span data-ttu-id="1d18a-104">Punkty końcowe skojarzenia są zdefiniowane jako część skojarzenia; Skojarzenie musi mieć dokładnie dwa punkty końcowe skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="1d18a-104">Association ends are defined as part of an association; an association must have exactly two association ends.</span></span> <span data-ttu-id="1d18a-105">[Właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) umożliwienia nawigacji z elementu end skojarzenia jednego do drugiego.</span><span class="sxs-lookup"><span data-stu-id="1d18a-105">[Navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) allow for navigation from one association end to the other.</span></span>  
  
 <span data-ttu-id="1d18a-106">Definicja end skojarzenia zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="1d18a-106">An association end definition contains the following information:</span></span>  
  
-   <span data-ttu-id="1d18a-107">Jeden z typów jednostek objętego skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="1d18a-107">One of the entity types involved in the association.</span></span> <span data-ttu-id="1d18a-108">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="1d18a-108">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1d18a-109">Dla danego skojarzenia typu jednostki, określony dla każdego końca skojarzenia może być taka sama.</span><span class="sxs-lookup"><span data-stu-id="1d18a-109">For a given association, the entity type specified for each association end can be the same.</span></span> <span data-ttu-id="1d18a-110">Spowoduje to utworzenie skojarzenia własny.</span><span class="sxs-lookup"><span data-stu-id="1d18a-110">This creates a self-association.</span></span>  
  
-   <span data-ttu-id="1d18a-111">[Skojarzenie liczebność zakończenia](../../../../docs/framework/data/adonet/association-end-multiplicity.md) oznacza liczbę wystąpień typów jednostek, które mogą być na jednym końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="1d18a-111">An [association end multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="1d18a-112">Skojarzenie liczebność zakończenia może mieć wartość jednego (1), zero lub jeden (od 0 do 1) lub wielu (\*).</span><span class="sxs-lookup"><span data-stu-id="1d18a-112">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span>  
  
-   <span data-ttu-id="1d18a-113">Nazwa dla elementu end skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="1d18a-113">A name for the association end.</span></span> <span data-ttu-id="1d18a-114">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="1d18a-114">(Optional)</span></span>  
  
-   <span data-ttu-id="1d18a-115">Informacje o operacjach wykonywanych na końcu skojarzenia, takich jak cascade przy usuwaniu.</span><span class="sxs-lookup"><span data-stu-id="1d18a-115">Information about operations that are performed on the association end, such as cascade on delete.</span></span> <span data-ttu-id="1d18a-116">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="1d18a-116">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d18a-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d18a-117">Example</span></span>  
 <span data-ttu-id="1d18a-118">Na poniższym diagramie przedstawiono modelu koncepcyjnego z dwóch skojarzenia: `PublishedBy` i `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="1d18a-118">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="1d18a-119">Punkty końcowe skojarzenia dla `PublishedBy` są skojarzenia `Book` i `Publisher` typy jednostek.</span><span class="sxs-lookup"><span data-stu-id="1d18a-119">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="1d18a-120">Liczebność `Publisher` punkt końcowy jest jeden (1) i liczebność `Book` punkt końcowy jest wiele (\*), informujący, że wydawca publikuje wiele książek i książkę są publikowane przez jednego wydawcy.</span><span class="sxs-lookup"><span data-stu-id="1d18a-120">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 <span data-ttu-id="1d18a-121">![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="1d18a-121">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="1d18a-122">ADO.NET Entity Framework używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="1d18a-122">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="1d18a-123">Definiuje CSDL poniżej `PublishedBy` skojarzenia pokazano na powyższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="1d18a-123">The CSDL below defines the `PublishedBy` association shown in the diagram above.</span></span> <span data-ttu-id="1d18a-124">Należy pamiętać, że typu, nazwy i liczebność każdego końca skojarzenia są określone przez atrybutów XML ( `Type`, `Role`, i `Multiplicity` atrybuty odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="1d18a-124">Note that the type, name, and multiplicity of each association end are specified by XML attributes (the `Type`, `Role`, and `Multiplicity` attributes, respectively).</span></span> <span data-ttu-id="1d18a-125">Dodatkowe informacje o operacji wykonywanych na końcu jest określony w elemencie XML ( `OnDelete` elementu).</span><span class="sxs-lookup"><span data-stu-id="1d18a-125">Optional information about operations performed on an end is specified in an XML element (the `OnDelete` element).</span></span> <span data-ttu-id="1d18a-126">W takim przypadku usunięcie wydawcy są wszystkie powiązane książek.</span><span class="sxs-lookup"><span data-stu-id="1d18a-126">In this case, if a publisher is deleted, so are all associated books.</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a><span data-ttu-id="1d18a-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d18a-127">See Also</span></span>  
 [<span data-ttu-id="1d18a-128">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="1d18a-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="1d18a-129">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="1d18a-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
