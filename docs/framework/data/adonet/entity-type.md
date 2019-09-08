---
title: typ jednostki
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: efd3ea0972148e885d4b22b49040640539bb28cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795120"
---
# <a name="entity-type"></a><span data-ttu-id="897e2-102">typ jednostki</span><span class="sxs-lookup"><span data-stu-id="897e2-102">entity type</span></span>
<span data-ttu-id="897e2-103">*Typ jednostki* jest podstawowym blokiem konstrukcyjnym opisującym strukturę danych z Entity Data Model (EDM).</span><span class="sxs-lookup"><span data-stu-id="897e2-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="897e2-104">W modelu koncepcyjnym typ jednostki reprezentuje strukturę koncepcji najwyższego poziomu, takich jak klienci lub zamówienia.</span><span class="sxs-lookup"><span data-stu-id="897e2-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="897e2-105">Typ jednostki to szablon wystąpień typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="897e2-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="897e2-106">Każdy szablon zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="897e2-106">Each template contains the following information:</span></span>  
  
- <span data-ttu-id="897e2-107">Unikatowa nazwa.</span><span class="sxs-lookup"><span data-stu-id="897e2-107">A unique name.</span></span> <span data-ttu-id="897e2-108">(Wymagane).</span><span class="sxs-lookup"><span data-stu-id="897e2-108">(Required.)</span></span>  
  
- <span data-ttu-id="897e2-109">[Klucz jednostki](entity-key.md) zdefiniowany przez jedną lub więcej właściwości.</span><span class="sxs-lookup"><span data-stu-id="897e2-109">An [entity key](entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="897e2-110">(Wymagane).</span><span class="sxs-lookup"><span data-stu-id="897e2-110">(Required.)</span></span>  
  
- <span data-ttu-id="897e2-111">Dane w postaci [Właściwości](property.md).</span><span class="sxs-lookup"><span data-stu-id="897e2-111">Data in the form of [properties](property.md).</span></span> <span data-ttu-id="897e2-112">(Opcjonalnie).</span><span class="sxs-lookup"><span data-stu-id="897e2-112">(Optional.)</span></span>  
  
- <span data-ttu-id="897e2-113">[Właściwości nawigacji](navigation-property.md) , które umożliwiają nawigację z jednego [końca](association-end.md) [skojarzenia](association-type.md) z drugim.</span><span class="sxs-lookup"><span data-stu-id="897e2-113">[Navigation properties](navigation-property.md) that allow for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="897e2-114">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="897e2-114">(Optional)</span></span>  
  
 <span data-ttu-id="897e2-115">W aplikacji wystąpienie typu jednostki reprezentuje określony obiekt (na przykład konkretny klient lub zamówienie).</span><span class="sxs-lookup"><span data-stu-id="897e2-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="897e2-116">Każde wystąpienie typu jednostki musi mieć unikatowy [klucz jednostki](entity-key.md) w ramach [zestawu jednostek](entity-set.md).</span><span class="sxs-lookup"><span data-stu-id="897e2-116">Each instance of an entity type must have a unique [entity key](entity-key.md) within an [entity set](entity-set.md).</span></span>  
  
 <span data-ttu-id="897e2-117">Dwa wystąpienia typu jednostki są uważane za równe tylko wtedy, gdy są one tego samego typu, a wartości ich kluczy jednostek są takie same.</span><span class="sxs-lookup"><span data-stu-id="897e2-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="897e2-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="897e2-118">Example</span></span>  
 <span data-ttu-id="897e2-119">Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`:</span><span class="sxs-lookup"><span data-stu-id="897e2-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 ![Przykładowy model z trzema typami jednostek](./media/entity-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="897e2-121">Należy zauważyć, że właściwości każdego typu jednostki, które tworzą swój klucz jednostki, są oznaczane "(kluczem)".</span><span class="sxs-lookup"><span data-stu-id="897e2-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="897e2-122">[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="897e2-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="897e2-123">Poniższy `Book` obiekt CSDL definiuje typ jednostki przedstawiony na poniższym diagramie:</span><span class="sxs-lookup"><span data-stu-id="897e2-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="897e2-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="897e2-124">See also</span></span>

- [<span data-ttu-id="897e2-125">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="897e2-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="897e2-126">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="897e2-126">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="897e2-127">aspekt</span><span class="sxs-lookup"><span data-stu-id="897e2-127">facet</span></span>](facet.md)
