---
title: Typ jednostki
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: cb542a1750a6b45dd2fca4d32501719470d9a78a
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410891"
---
# <a name="entity-type"></a><span data-ttu-id="bca00-102">Typ jednostki</span><span class="sxs-lookup"><span data-stu-id="bca00-102">entity type</span></span>
<span data-ttu-id="bca00-103">*Typu jednostki* jest elementem składowym podstawowych do opisywania struktury danych z Entity Data Model (EDM).</span><span class="sxs-lookup"><span data-stu-id="bca00-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="bca00-104">W modelu koncepcyjnym typ jednostki reprezentuje strukturę koncepcje najwyższego poziomu, takich jak klienci i zamówienia.</span><span class="sxs-lookup"><span data-stu-id="bca00-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="bca00-105">Typ jednostki jest szablonem dla wystąpienia typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="bca00-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="bca00-106">Każdy szablon zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="bca00-106">Each template contains the following information:</span></span>  
  
-   <span data-ttu-id="bca00-107">Unikatowa nazwa.</span><span class="sxs-lookup"><span data-stu-id="bca00-107">A unique name.</span></span> <span data-ttu-id="bca00-108">(Wymagane).</span><span class="sxs-lookup"><span data-stu-id="bca00-108">(Required.)</span></span>  
  
-   <span data-ttu-id="bca00-109">[Klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) zdefiniowane przez jedną lub więcej właściwości.</span><span class="sxs-lookup"><span data-stu-id="bca00-109">An [entity key](../../../../docs/framework/data/adonet/entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="bca00-110">(Wymagane).</span><span class="sxs-lookup"><span data-stu-id="bca00-110">(Required.)</span></span>  
  
-   <span data-ttu-id="bca00-111">Dane w postaci [właściwości](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="bca00-111">Data in the form of [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="bca00-112">(Opcjonalnie).</span><span class="sxs-lookup"><span data-stu-id="bca00-112">(Optional.)</span></span>  
  
-   <span data-ttu-id="bca00-113">[Właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) umożliwiające nawigacji z jednego [zakończenia](../../../../docs/framework/data/adonet/association-end.md) z [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) w innym celu.</span><span class="sxs-lookup"><span data-stu-id="bca00-113">[Navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) that allow for navigation from one [end](../../../../docs/framework/data/adonet/association-end.md) of an [association](../../../../docs/framework/data/adonet/association-type.md) to the other end.</span></span> <span data-ttu-id="bca00-114">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="bca00-114">(Optional)</span></span>  
  
 <span data-ttu-id="bca00-115">W aplikacji wystąpienia typu jednostki reprezentuje określonego obiektu (na przykład konkretnego klienta lub zamówienia).</span><span class="sxs-lookup"><span data-stu-id="bca00-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="bca00-116">Każde wystąpienie typu jednostki musi mieć unikatową [klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) w ramach [zestaw jednostek](../../../../docs/framework/data/adonet/entity-set.md).</span><span class="sxs-lookup"><span data-stu-id="bca00-116">Each instance of an entity type must have a unique [entity key](../../../../docs/framework/data/adonet/entity-key.md) within an [entity set](../../../../docs/framework/data/adonet/entity-set.md).</span></span>  
  
 <span data-ttu-id="bca00-117">Dwa wystąpienia typu jednostki są traktowane jako równe tylko wtedy, gdy są one tego samego typu i wartości kluczy podmiotu są takie same.</span><span class="sxs-lookup"><span data-stu-id="bca00-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bca00-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="bca00-118">Example</span></span>  
 <span data-ttu-id="bca00-119">Poniższy diagram przedstawia modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`:</span><span class="sxs-lookup"><span data-stu-id="bca00-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 ![Przykładowy model przy użyciu trzech typów jednostek](./media/entity-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="bca00-121">Należy pamiętać, że właściwości każdego typu jednostki, które tworzą klucz jednostki są oznaczone symbolem "(klucz)".</span><span class="sxs-lookup"><span data-stu-id="bca00-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="bca00-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="bca00-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="bca00-123">Definiuje następujące CSDL `Book` typu jednostki, które pokazano na powyższym diagramie:</span><span class="sxs-lookup"><span data-stu-id="bca00-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="bca00-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bca00-124">See also</span></span>
- [<span data-ttu-id="bca00-125">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="bca00-125">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="bca00-126">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="bca00-126">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
- [<span data-ttu-id="bca00-127">aspekt</span><span class="sxs-lookup"><span data-stu-id="bca00-127">facet</span></span>](../../../../docs/framework/data/adonet/facet.md)
