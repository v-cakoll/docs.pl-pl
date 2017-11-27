---
title: "skojarzenie liczebność zakończenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3d6071b2dfab4a1f057c9e04b84e1163fb0a53c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="68e1d-102">skojarzenie liczebność zakończenia</span><span class="sxs-lookup"><span data-stu-id="68e1d-102">association end multiplicity</span></span>
<span data-ttu-id="68e1d-103">*Skojarzenie liczebność zakończenia* definiuje liczbę [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) wystąpień, które mogą być na końcu jednego [skojarzenia](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="68e1d-103">*Association end multiplicity* defines the number of [entity type](../../../../docs/framework/data/adonet/entity-type.md) instances that can be at one end of an [association](../../../../docs/framework/data/adonet/association-type.md).</span></span>  
  
 <span data-ttu-id="68e1d-104">Skojarzenie liczebność zakończenia może mieć jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="68e1d-104">An association end multiplicity can have one of the following values:</span></span>  
  
-   <span data-ttu-id="68e1d-105">jednego (1): wskazuje danego wystąpienia typu dokładnie jednego obiektu występuje na końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="68e1d-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
-   <span data-ttu-id="68e1d-106">zero lub jeden (od 0 do 1): oznacza, że na końcu skojarzenia zero lub jeden wystąpień typów jednostek.</span><span class="sxs-lookup"><span data-stu-id="68e1d-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
-   <span data-ttu-id="68e1d-107">wiele (*): oznacza, że zero, jeden lub więcej wystąpień typów jednostek na końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="68e1d-107">many (*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="68e1d-108">Skojarzenie często jest określony przez jego liczebność punktów końcowych skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="68e1d-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="68e1d-109">Na przykład jeśli końce skojarzenie Liczebność punktów jednego (1), a wiele (*), skojarzenie nazywa się skojarzenia typu jeden do wielu.</span><span class="sxs-lookup"><span data-stu-id="68e1d-109">For example, if the ends of an association have multiplicities one (1) and many (*), the association is called a one-to-many association.</span></span> <span data-ttu-id="68e1d-110">W poniższym przykładzie `PublishedBy` association jest skojarzeniem jeden do wielu (wydawca publikuje wiele książek i książkę są publikowane przez jednego wydawcy).</span><span class="sxs-lookup"><span data-stu-id="68e1d-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="68e1d-111">`WrittenBy` Association jest skojarzeniem wiele do wielu (książkę może mieć wielu autorów i Autor może zapisywać wiele książek).</span><span class="sxs-lookup"><span data-stu-id="68e1d-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68e1d-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="68e1d-112">Example</span></span>  
 <span data-ttu-id="68e1d-113">Na poniższym diagramie przedstawiono modelu koncepcyjnego z dwóch skojarzenia: `PublishedBy` i `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="68e1d-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="68e1d-114">Punkty końcowe skojarzenia dla `PublishedBy` są skojarzenia `Book` i `Publisher` typy jednostek.</span><span class="sxs-lookup"><span data-stu-id="68e1d-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="68e1d-115">Liczebność `Publisher` punkt końcowy jest jeden (1) i liczebność `Book` punkt końcowy jest wiele (*).</span><span class="sxs-lookup"><span data-stu-id="68e1d-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (*).</span></span>  
  
 <span data-ttu-id="68e1d-116">![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="68e1d-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="68e1d-117">ADO.NET Entity Framework używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="68e1d-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="68e1d-118">Definiuje następujące CSDL `PublishedBy` skojarzenia pokazano na powyższym diagramie:</span><span class="sxs-lookup"><span data-stu-id="68e1d-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="68e1d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68e1d-119">See Also</span></span>  
 [<span data-ttu-id="68e1d-120">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="68e1d-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="68e1d-121">Modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="68e1d-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
