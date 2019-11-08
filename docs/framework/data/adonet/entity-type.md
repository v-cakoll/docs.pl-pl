---
title: typ jednostki
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: 1dafce5f7f95ba6f391c8742944f40a9afa7dcf8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737802"
---
# <a name="entity-type"></a><span data-ttu-id="36c3d-102">typ jednostki</span><span class="sxs-lookup"><span data-stu-id="36c3d-102">entity type</span></span>
<span data-ttu-id="36c3d-103">*Typ jednostki* jest podstawowym blokiem konstrukcyjnym opisującym strukturę danych z Entity Data Model (EDM).</span><span class="sxs-lookup"><span data-stu-id="36c3d-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="36c3d-104">W modelu koncepcyjnym typ jednostki reprezentuje strukturę koncepcji najwyższego poziomu, takich jak klienci lub zamówienia.</span><span class="sxs-lookup"><span data-stu-id="36c3d-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="36c3d-105">Typ jednostki to szablon wystąpień typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="36c3d-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="36c3d-106">Każdy szablon zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="36c3d-106">Each template contains the following information:</span></span>  
  
- <span data-ttu-id="36c3d-107">Unikatowa nazwa.</span><span class="sxs-lookup"><span data-stu-id="36c3d-107">A unique name.</span></span> <span data-ttu-id="36c3d-108">(Wymagane).</span><span class="sxs-lookup"><span data-stu-id="36c3d-108">(Required.)</span></span>  
  
- <span data-ttu-id="36c3d-109">[Klucz jednostki](entity-key.md) zdefiniowany przez jedną lub więcej właściwości.</span><span class="sxs-lookup"><span data-stu-id="36c3d-109">An [entity key](entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="36c3d-110">(Wymagane).</span><span class="sxs-lookup"><span data-stu-id="36c3d-110">(Required.)</span></span>  
  
- <span data-ttu-id="36c3d-111">Dane w postaci [Właściwości](property.md).</span><span class="sxs-lookup"><span data-stu-id="36c3d-111">Data in the form of [properties](property.md).</span></span> <span data-ttu-id="36c3d-112">(Opcjonalnie).</span><span class="sxs-lookup"><span data-stu-id="36c3d-112">(Optional.)</span></span>  
  
- <span data-ttu-id="36c3d-113">[Właściwości nawigacji](navigation-property.md) , które umożliwiają nawigację z jednego [końca](association-end.md) [skojarzenia](association-type.md) z drugim.</span><span class="sxs-lookup"><span data-stu-id="36c3d-113">[Navigation properties](navigation-property.md) that allow for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="36c3d-114">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="36c3d-114">(Optional)</span></span>  
  
 <span data-ttu-id="36c3d-115">W aplikacji wystąpienie typu jednostki reprezentuje określony obiekt (na przykład konkretny klient lub zamówienie).</span><span class="sxs-lookup"><span data-stu-id="36c3d-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="36c3d-116">Każde wystąpienie typu jednostki musi mieć unikatowy [klucz jednostki](entity-key.md) w ramach [zestawu jednostek](entity-set.md).</span><span class="sxs-lookup"><span data-stu-id="36c3d-116">Each instance of an entity type must have a unique [entity key](entity-key.md) within an [entity set](entity-set.md).</span></span>  
  
 <span data-ttu-id="36c3d-117">Dwa wystąpienia typu jednostki są uważane za równe tylko wtedy, gdy są one tego samego typu, a wartości ich kluczy jednostek są takie same.</span><span class="sxs-lookup"><span data-stu-id="36c3d-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36c3d-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="36c3d-118">Example</span></span>  
 <span data-ttu-id="36c3d-119">Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`:</span><span class="sxs-lookup"><span data-stu-id="36c3d-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 ![Przykładowy model z trzema typami jednostek](./media/entity-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="36c3d-121">Należy zauważyć, że właściwości każdego typu jednostki, które tworzą swój klucz jednostki, są oznaczane "(kluczem)".</span><span class="sxs-lookup"><span data-stu-id="36c3d-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="36c3d-122">[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="36c3d-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="36c3d-123">Następujący identyfikator CSDL definiuje typ jednostki `Book` przedstawiony na poniższym diagramie:</span><span class="sxs-lookup"><span data-stu-id="36c3d-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="36c3d-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36c3d-124">See also</span></span>

- [<span data-ttu-id="36c3d-125">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="36c3d-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="36c3d-126">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="36c3d-126">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="36c3d-127">aspekt</span><span class="sxs-lookup"><span data-stu-id="36c3d-127">facet</span></span>](facet.md)
