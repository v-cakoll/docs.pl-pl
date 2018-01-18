---
title: "Typ powiązania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5349889017ea23701a17a92947d9750610a52f59
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="association-type"></a><span data-ttu-id="6d5e4-102">Typ powiązania</span><span class="sxs-lookup"><span data-stu-id="6d5e4-102">association type</span></span>
<span data-ttu-id="6d5e4-103">*Typ skojarzenia* (nazywanych również skojarzenie) jest podstawowym blokiem opisu relacje w modelu danych jednostki (EDM).</span><span class="sxs-lookup"><span data-stu-id="6d5e4-103">An *association type* (also called an association) is the fundamental building block for describing relationships in the Entity Data Model (EDM).</span></span> <span data-ttu-id="6d5e4-104">W modelu koncepcyjnym, skojarzenie reprezentuje relację między dwiema [typów jednostek](../../../../docs/framework/data/adonet/entity-type.md) (takich jak `Customer` i `Order`).</span><span class="sxs-lookup"><span data-stu-id="6d5e4-104">In a conceptual model, an association represents a relationship between two [entity types](../../../../docs/framework/data/adonet/entity-type.md) (such as `Customer` and `Order`).</span></span> <span data-ttu-id="6d5e4-105">W aplikacji, wystąpienie skojarzenia reprezentuje określone skojarzenia (takie jak skojarzenie między wystąpieniem `Customer` i wystąpienie `Order`).</span><span class="sxs-lookup"><span data-stu-id="6d5e4-105">In an application, an instance of an association represents a specific association (such as an association between an instance of `Customer` and an instance of `Order`).</span></span> <span data-ttu-id="6d5e4-106">Skojarzenie wystąpienia są logicznie pogrupowane w [zestawu skojarzeń](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="6d5e4-106">Association instances are logically grouped in an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span>  
  
 <span data-ttu-id="6d5e4-107">Definicja skojarzenia zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="6d5e4-107">An association definition contains the following information:</span></span>  
  
-   <span data-ttu-id="6d5e4-108">Unikatowa nazwa.</span><span class="sxs-lookup"><span data-stu-id="6d5e4-108">A unique name.</span></span> <span data-ttu-id="6d5e4-109">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="6d5e4-109">(Required)</span></span>  
  
-   <span data-ttu-id="6d5e4-110">Dwa [skojarzenia](../../../../docs/framework/data/adonet/association-end.md), jeden dla poszczególnych typów jednostek w relacji.</span><span class="sxs-lookup"><span data-stu-id="6d5e4-110">Two [association ends](../../../../docs/framework/data/adonet/association-end.md), one for each entity type in the relationship.</span></span> <span data-ttu-id="6d5e4-111">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="6d5e4-111">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d5e4-112">Skojarzenie nie może reprezentować relację między więcej niż dwa typy jednostek.</span><span class="sxs-lookup"><span data-stu-id="6d5e4-112">An association cannot represent a relationship among more than two entity types.</span></span> <span data-ttu-id="6d5e4-113">Skojarzenie można jednak zdefiniować relację samoobsługowego, określając ten sam typ jednostki dla każdego z jego punkty końcowe skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="6d5e4-113">An association can, however, define a self-relationship by specifying the same entity type for each of its association ends.</span></span>  
  
-   <span data-ttu-id="6d5e4-114">A [ograniczenia integralności referencyjnej](../../../../docs/framework/data/adonet/referential-integrity-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="6d5e4-114">A [referential integrity constraint](../../../../docs/framework/data/adonet/referential-integrity-constraint.md).</span></span> <span data-ttu-id="6d5e4-115">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="6d5e4-115">(Optional)</span></span>  
  
 <span data-ttu-id="6d5e4-116">Koniec każdego skojarzenia należy określić [skojarzenie liczebność zakończenia](../../../../docs/framework/data/adonet/association-end-multiplicity.md) oznacza liczbę wystąpień typów jednostek, które mogą być na jednym końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="6d5e4-116">Each association end must specify an [association end multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="6d5e4-117">Skojarzenie liczebność zakończenia może mieć wartość jednego (1), zero lub jeden (od 0 do 1) lub wielu (\*).</span><span class="sxs-lookup"><span data-stu-id="6d5e4-117">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span> <span data-ttu-id="6d5e4-118">Wystąpień typów jednostek w jeden element end skojarzenia jest możliwy za pośrednictwem [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) lub kluczy obcych, jeśli są one dostępne w ramach typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="6d5e4-118">Entity type instances at one end of an association can be accessed through [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) or foreign keys if they are exposed on an entity type.</span></span> <span data-ttu-id="6d5e4-119">Aby uzyskać więcej informacji, zobacz [modelu Entity Data Model: klucze obce](../../../../docs/framework/data/adonet/foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="6d5e4-119">For more information, see [Entity Data Model: Foreign Keys](../../../../docs/framework/data/adonet/foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d5e4-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d5e4-120">Example</span></span>  
 <span data-ttu-id="6d5e4-121">Na poniższym diagramie przedstawiono modelu koncepcyjnego z dwóch skojarzenia: `PublishedBy` i `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="6d5e4-121">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="6d5e4-122">Punkty końcowe skojarzenia dla `PublishedBy` są skojarzenia `Book` i `Publisher` typy jednostek.</span><span class="sxs-lookup"><span data-stu-id="6d5e4-122">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="6d5e4-123">Liczebność `Publisher` punkt końcowy jest jeden (1) i liczebność `Book` punkt końcowy jest wiele (\*), informujący, że wydawca publikuje wiele książek i książkę są publikowane przez jednego wydawcy.</span><span class="sxs-lookup"><span data-stu-id="6d5e4-123">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 <span data-ttu-id="6d5e4-124">![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="6d5e4-124">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="6d5e4-125">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="6d5e4-125">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="6d5e4-126">Definiuje następujące CSDL `PublishedBy` skojarzenia pokazano na powyższym diagramie:</span><span class="sxs-lookup"><span data-stu-id="6d5e4-126">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="6d5e4-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d5e4-127">See Also</span></span>  
 [<span data-ttu-id="6d5e4-128">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="6d5e4-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="6d5e4-129">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="6d5e4-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
