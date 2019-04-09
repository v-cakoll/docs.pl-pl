---
title: skojarzenie i liczebność
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 59eed56204543adf405cfc7c71a49697a9e18374
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135034"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="a0297-102">skojarzenie i liczebność</span><span class="sxs-lookup"><span data-stu-id="a0297-102">association end multiplicity</span></span>
<span data-ttu-id="a0297-103">*Skojarzenie i liczebność* definiuje liczbę [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) wystąpień, które mogą być na jednym końcu [skojarzenie](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="a0297-103">*Association end multiplicity* defines the number of [entity type](../../../../docs/framework/data/adonet/entity-type.md) instances that can be at one end of an [association](../../../../docs/framework/data/adonet/association-type.md).</span></span>  
  
 <span data-ttu-id="a0297-104">Skojarzenie i liczebność może mieć jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="a0297-104">An association end multiplicity can have one of the following values:</span></span>  
  
-   <span data-ttu-id="a0297-105">jeden (1): Wskazuje, że to wystąpienie typu dokładnie jednej jednostki znajduje się na końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="a0297-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
-   <span data-ttu-id="a0297-106">zero lub jeden (od 0 do 1): Oznacza, że na końcu skojarzenia zera lub jednego wystąpienia typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="a0297-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
-   <span data-ttu-id="a0297-107">wiele (\*): oznacza, że wartość zero, jeden lub więcej wystąpień typu jednostki na końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="a0297-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="a0297-108">Skojarzenie często jest określony przez jego liczebność punktów końcowych skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="a0297-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="a0297-109">Na przykład, jeśli Liczebność punktów jeden (1) i jest wiele końcach asocjacji (\*), skojarzenia nosi nazwę skojarzenia typu jeden do wielu.</span><span class="sxs-lookup"><span data-stu-id="a0297-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="a0297-110">W poniższym przykładzie `PublishedBy` skojarzenie jest skojarzenia typu jeden do wielu (wydawca publikuje wiele książek i książki opublikowana przez jedną wydawcą).</span><span class="sxs-lookup"><span data-stu-id="a0297-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="a0297-111">`WrittenBy` Skojarzenie jest skojarzenie wiele do wielu (książki może mieć wielu autorów i Autor może zapisywać wiele książek).</span><span class="sxs-lookup"><span data-stu-id="a0297-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0297-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0297-112">Example</span></span>  
 <span data-ttu-id="a0297-113">Poniższy diagram przedstawia modelu koncepcyjnego z dwóch skojarzeń: `PublishedBy` i `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="a0297-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="a0297-114">Punkty końcowe dla skojarzenia `PublishedBy` to skojarzenie `Book` i `Publisher` typów jednostek.</span><span class="sxs-lookup"><span data-stu-id="a0297-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="a0297-115">Liczebność `Publisher` end jest jeden (1), a liczebność `Book` end jest wiele (\*).</span><span class="sxs-lookup"><span data-stu-id="a0297-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 ![Przykładowy model przy użyciu trzech typów jednostek](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="a0297-117">ADO.NET Entity Framework używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="a0297-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="a0297-118">Definiuje następujące CSDL `PublishedBy` skojarzenia pokazano na powyższym diagramie:</span><span class="sxs-lookup"><span data-stu-id="a0297-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="a0297-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0297-119">See also</span></span>

- [<span data-ttu-id="a0297-120">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="a0297-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="a0297-121">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="a0297-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
