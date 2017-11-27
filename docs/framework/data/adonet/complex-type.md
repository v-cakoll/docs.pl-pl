---
title: "Typ złożony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 389a3be7342005e424c89ff4e430b4a257f2da5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="complex-type"></a><span data-ttu-id="8c5ac-102">Typ złożony</span><span class="sxs-lookup"><span data-stu-id="8c5ac-102">complex type</span></span>
<span data-ttu-id="8c5ac-103">A *typu złożonego* szablonem służącym do definiowania właściwości rozbudowane, strukturalnych na [typów jednostek](../../../../docs/framework/data/adonet/entity-type.md) lub na inne typy złożone.</span><span class="sxs-lookup"><span data-stu-id="8c5ac-103">A *complex type* is a template for defining rich, structured properties on [entity types](../../../../docs/framework/data/adonet/entity-type.md) or on other complex types.</span></span> <span data-ttu-id="8c5ac-104">Każdy szablon zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="8c5ac-104">Each template contains the following:</span></span>  
  
-   <span data-ttu-id="8c5ac-105">Unikatowa nazwa.</span><span class="sxs-lookup"><span data-stu-id="8c5ac-105">A unique name.</span></span> <span data-ttu-id="8c5ac-106">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="8c5ac-106">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8c5ac-107">Nazwa typu złożonego nie może być taka sama jak nazwa typu jednostki w ramach tego samego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="8c5ac-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
-   <span data-ttu-id="8c5ac-108">Dane w postaci jednego lub więcej [właściwości](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="8c5ac-108">Data in the form of one or more [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="8c5ac-109">(Opcjonalnie).</span><span class="sxs-lookup"><span data-stu-id="8c5ac-109">(Optional.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8c5ac-110">Właściwość typu złożonego może być inny typ złożony.</span><span class="sxs-lookup"><span data-stu-id="8c5ac-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="8c5ac-111">Typ złożony jest podobny do typu jednostki, w tym typie złożonym może przenosić ładunku danych w formie właściwości typu pierwotnego lub innych typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="8c5ac-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="8c5ac-112">Istnieją jednak niektóre podstawowe różnice między typy jednostek i typów złożonych:</span><span class="sxs-lookup"><span data-stu-id="8c5ac-112">However, there are some key differences between complex types and entity types:</span></span>  
  
-   <span data-ttu-id="8c5ac-113">Typy złożone nie mają tożsamości i dlatego nie może istnieć niezależnie.</span><span class="sxs-lookup"><span data-stu-id="8c5ac-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="8c5ac-114">Typy złożone może istnieć tylko jako właściwości na typy jednostek i innych typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="8c5ac-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
-   <span data-ttu-id="8c5ac-115">Typy złożone nie może brać udziału w [skojarzenia](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="8c5ac-115">Complex types cannot participate in [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="8c5ac-116">Żadna końca skojarzenia może być typem złożonym i w związku z tym [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) nie może być zdefiniowana dla typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="8c5ac-116">Neither end of an association can be a complex type, and therefore [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c5ac-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c5ac-117">Example</span></span>  
 <span data-ttu-id="8c5ac-118">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="8c5ac-118">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="8c5ac-119">Następujący plik CSDL definiuje typ złożony, adres, z właściwością typu pierwotnego `StreetAddress`, `City`, `StateOrProvince`, `Country`, i `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="8c5ac-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="8c5ac-120">Aby zdefiniować typu złożonego `Address` (powyżej) jako właściwość typu jednostki, należy zadeklarować typ właściwości w definicji typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="8c5ac-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="8c5ac-121">Deklaruje następującego pliku CSDL `Address` właściwości jako typ złożony w ramach typu jednostki (wydawcy):</span><span class="sxs-lookup"><span data-stu-id="8c5ac-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="8c5ac-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c5ac-122">See Also</span></span>  
 [<span data-ttu-id="8c5ac-123">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="8c5ac-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="8c5ac-124">Modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="8c5ac-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
