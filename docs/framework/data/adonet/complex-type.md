---
title: typ złożony
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: fac25ace69938e1245200e10285f4460ac216780
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948734"
---
# <a name="complex-type"></a><span data-ttu-id="6be5d-102">typ złożony</span><span class="sxs-lookup"><span data-stu-id="6be5d-102">complex type</span></span>
<span data-ttu-id="6be5d-103">*Typ złożony* to szablon służący do definiowania bogatych, strukturalnych właściwości w [typach jednostek](../../../../docs/framework/data/adonet/entity-type.md) lub w innych typach złożonych.</span><span class="sxs-lookup"><span data-stu-id="6be5d-103">A *complex type* is a template for defining rich, structured properties on [entity types](../../../../docs/framework/data/adonet/entity-type.md) or on other complex types.</span></span> <span data-ttu-id="6be5d-104">Każdy szablon zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="6be5d-104">Each template contains the following:</span></span>  
  
- <span data-ttu-id="6be5d-105">Unikatowa nazwa.</span><span class="sxs-lookup"><span data-stu-id="6be5d-105">A unique name.</span></span> <span data-ttu-id="6be5d-106">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="6be5d-106">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6be5d-107">Nazwa typu złożonego nie może być taka sama jak nazwa typu jednostki w obrębie tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6be5d-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
- <span data-ttu-id="6be5d-108">Dane w postaci jednej lub wielu [Właściwości](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="6be5d-108">Data in the form of one or more [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="6be5d-109">(Opcjonalnie).</span><span class="sxs-lookup"><span data-stu-id="6be5d-109">(Optional.)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6be5d-110">Właściwość typu złożonego może być innym typem złożonym.</span><span class="sxs-lookup"><span data-stu-id="6be5d-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="6be5d-111">Typ złożony jest podobny do typu jednostki, w którym typ złożony może przenosić ładunek danych w postaci właściwości typu pierwotnego lub innych typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="6be5d-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="6be5d-112">Istnieją jednak pewne kluczowe różnice między typami złożonymi i typami jednostek:</span><span class="sxs-lookup"><span data-stu-id="6be5d-112">However, there are some key differences between complex types and entity types:</span></span>  
  
- <span data-ttu-id="6be5d-113">Typy złożone nie mają tożsamości i w związku z tym nie mogą istnieć niezależnie.</span><span class="sxs-lookup"><span data-stu-id="6be5d-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="6be5d-114">Typy złożone mogą istnieć tylko jako właściwości typów jednostek lub innych typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="6be5d-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
- <span data-ttu-id="6be5d-115">Typy złożone nie mogą uczestniczyć [](../../../../docs/framework/data/adonet/association-type.md)w skojarzeniach.</span><span class="sxs-lookup"><span data-stu-id="6be5d-115">Complex types cannot participate in [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="6be5d-116">Żadne zakończenie skojarzenia nie może być typem złożonym, dlatego [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) nie mogą być zdefiniowane w typach złożonych.</span><span class="sxs-lookup"><span data-stu-id="6be5d-116">Neither end of an association can be a complex type, and therefore [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6be5d-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="6be5d-117">Example</span></span>  
 <span data-ttu-id="6be5d-118">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="6be5d-118">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="6be5d-119">Następujący CSDL definiuje typ złożony, adres, z `StreetAddress`właściwościami typu pierwotnego, `City`, `StateOrProvince` `Country`,, i `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="6be5d-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="6be5d-120">Aby zdefiniować typ `Address` złożony (powyżej) jako właściwość typu jednostki, należy zadeklarować typ właściwości w definicji typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="6be5d-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="6be5d-121">Następujący CSDL deklaruje `Address` właściwość jako typ złożony dla typu jednostki (wydawca):</span><span class="sxs-lookup"><span data-stu-id="6be5d-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="6be5d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6be5d-122">See also</span></span>

- [<span data-ttu-id="6be5d-123">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="6be5d-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="6be5d-124">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="6be5d-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
