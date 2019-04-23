---
title: typ złożony
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 9d63660c441192bbc9ecb48bb3a86030b46461cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160813"
---
# <a name="complex-type"></a><span data-ttu-id="d815c-102">typ złożony</span><span class="sxs-lookup"><span data-stu-id="d815c-102">complex type</span></span>
<span data-ttu-id="d815c-103">A *typu złożonego* jest szablon służący do definiowania właściwości zaawansowane, ze strukturą na [typów jednostek](../../../../docs/framework/data/adonet/entity-type.md) lub na inne typy złożone.</span><span class="sxs-lookup"><span data-stu-id="d815c-103">A *complex type* is a template for defining rich, structured properties on [entity types](../../../../docs/framework/data/adonet/entity-type.md) or on other complex types.</span></span> <span data-ttu-id="d815c-104">Każdy szablon zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="d815c-104">Each template contains the following:</span></span>  
  
-   <span data-ttu-id="d815c-105">Unikatowa nazwa.</span><span class="sxs-lookup"><span data-stu-id="d815c-105">A unique name.</span></span> <span data-ttu-id="d815c-106">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="d815c-106">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d815c-107">Nazwa typu złożonego nie może być taka sama jak nazwa typu jednostki w ramach tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d815c-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
-   <span data-ttu-id="d815c-108">Dane w postaci jednego lub więcej [właściwości](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="d815c-108">Data in the form of one or more [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="d815c-109">(Opcjonalnie).</span><span class="sxs-lookup"><span data-stu-id="d815c-109">(Optional.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d815c-110">Właściwość typu złożonego, może być innego typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="d815c-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="d815c-111">Typ złożony jest podobny dla typu jednostki, w tym, że typ złożony mogą przenosić ładunek danych w formie właściwości typu pierwotnego lub inne typy złożone.</span><span class="sxs-lookup"><span data-stu-id="d815c-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="d815c-112">Jednakże istnieją niektóre podstawowe różnice między typy złożone i typy jednostek:</span><span class="sxs-lookup"><span data-stu-id="d815c-112">However, there are some key differences between complex types and entity types:</span></span>  
  
-   <span data-ttu-id="d815c-113">Typy złożone nie mają tożsamości i dlatego nie mogą istnieć niezależnie.</span><span class="sxs-lookup"><span data-stu-id="d815c-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="d815c-114">Typy złożone może istnieć tylko jako właściwości na typy jednostek lub inne typy złożone.</span><span class="sxs-lookup"><span data-stu-id="d815c-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
-   <span data-ttu-id="d815c-115">Typy złożone nie mogą uczestniczyć w [skojarzenia](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="d815c-115">Complex types cannot participate in [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="d815c-116">Żadna end elementu association może być typem złożonym i w związku z tym [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) nie można definiować dla typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="d815c-116">Neither end of an association can be a complex type, and therefore [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d815c-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="d815c-117">Example</span></span>  
 <span data-ttu-id="d815c-118">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="d815c-118">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="d815c-119">Następujące CSDL definiuje typ złożony, adres, z właściwościami typu pierwotnego `StreetAddress`, `City`, `StateOrProvince`, `Country`, i `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="d815c-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="d815c-120">Aby zdefiniować typ złożony `Address` (p. wyżej) jako właściwość typu encji należy zadeklarować typ właściwości w definicji typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="d815c-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="d815c-121">Deklaruje następujące CSDL `Address` właściwość typu złożonego typu encji (wydawcy):</span><span class="sxs-lookup"><span data-stu-id="d815c-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="d815c-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d815c-122">See also</span></span>

- [<span data-ttu-id="d815c-123">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="d815c-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="d815c-124">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="d815c-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
