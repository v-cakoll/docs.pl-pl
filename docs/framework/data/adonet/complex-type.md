---
title: typ złożony
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 0d9b8efd08cc0dfba5b26a70773b614b0d63d74f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786745"
---
# <a name="complex-type"></a><span data-ttu-id="5d5a0-102">typ złożony</span><span class="sxs-lookup"><span data-stu-id="5d5a0-102">complex type</span></span>
<span data-ttu-id="5d5a0-103">*Typ złożony* to szablon służący do definiowania bogatych, strukturalnych właściwości w [typach jednostek](entity-type.md) lub w innych typach złożonych.</span><span class="sxs-lookup"><span data-stu-id="5d5a0-103">A *complex type* is a template for defining rich, structured properties on [entity types](entity-type.md) or on other complex types.</span></span> <span data-ttu-id="5d5a0-104">Każdy szablon zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5d5a0-104">Each template contains the following:</span></span>  
  
- <span data-ttu-id="5d5a0-105">Unikatowa nazwa.</span><span class="sxs-lookup"><span data-stu-id="5d5a0-105">A unique name.</span></span> <span data-ttu-id="5d5a0-106">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="5d5a0-106">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5d5a0-107">Nazwa typu złożonego nie może być taka sama jak nazwa typu jednostki w obrębie tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5d5a0-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
- <span data-ttu-id="5d5a0-108">Dane w postaci jednej lub wielu [Właściwości](property.md).</span><span class="sxs-lookup"><span data-stu-id="5d5a0-108">Data in the form of one or more [properties](property.md).</span></span> <span data-ttu-id="5d5a0-109">(Opcjonalnie).</span><span class="sxs-lookup"><span data-stu-id="5d5a0-109">(Optional.)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5d5a0-110">Właściwość typu złożonego może być innym typem złożonym.</span><span class="sxs-lookup"><span data-stu-id="5d5a0-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="5d5a0-111">Typ złożony jest podobny do typu jednostki, w którym typ złożony może przenosić ładunek danych w postaci właściwości typu pierwotnego lub innych typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="5d5a0-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="5d5a0-112">Istnieją jednak pewne kluczowe różnice między typami złożonymi i typami jednostek:</span><span class="sxs-lookup"><span data-stu-id="5d5a0-112">However, there are some key differences between complex types and entity types:</span></span>  
  
- <span data-ttu-id="5d5a0-113">Typy złożone nie mają tożsamości i w związku z tym nie mogą istnieć niezależnie.</span><span class="sxs-lookup"><span data-stu-id="5d5a0-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="5d5a0-114">Typy złożone mogą istnieć tylko jako właściwości typów jednostek lub innych typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="5d5a0-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
- <span data-ttu-id="5d5a0-115">Typy złożone nie mogą uczestniczyć w [skojarzeniach](association-type.md).</span><span class="sxs-lookup"><span data-stu-id="5d5a0-115">Complex types cannot participate in [associations](association-type.md).</span></span> <span data-ttu-id="5d5a0-116">Żadne zakończenie skojarzenia nie może być typem złożonym, dlatego [właściwości nawigacji](navigation-property.md) nie mogą być zdefiniowane w typach złożonych.</span><span class="sxs-lookup"><span data-stu-id="5d5a0-116">Neither end of an association can be a complex type, and therefore [navigation properties](navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d5a0-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d5a0-117">Example</span></span>  
 <span data-ttu-id="5d5a0-118">[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="5d5a0-118">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="5d5a0-119">Następujący CSDL definiuje typ złożony, adres, z `StreetAddress`właściwościami typu pierwotnego, `City`, `StateOrProvince` `Country`,, i `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="5d5a0-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="5d5a0-120">Aby zdefiniować typ `Address` złożony (powyżej) jako właściwość typu jednostki, należy zadeklarować typ właściwości w definicji typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="5d5a0-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="5d5a0-121">Następujący CSDL deklaruje `Address` właściwość jako typ złożony dla typu jednostki (wydawca):</span><span class="sxs-lookup"><span data-stu-id="5d5a0-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="5d5a0-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d5a0-122">See also</span></span>

- [<span data-ttu-id="5d5a0-123">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="5d5a0-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="5d5a0-124">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="5d5a0-124">Entity Data Model</span></span>](entity-data-model.md)
