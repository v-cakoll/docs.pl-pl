---
title: ograniczenie integralności referencyjnej
description: Dowiedz się więcej na temat ograniczeń więzów integralności w Entity Data Model, co gwarantuje, że poprawne skojarzenia zawsze istnieją między typami jednostek.
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: 65c811b2a12a64870107ff771d5acc64e86f2c1f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286627"
---
# <a name="referential-integrity-constraint"></a><span data-ttu-id="bde76-103">ograniczenie integralności referencyjnej</span><span class="sxs-lookup"><span data-stu-id="bde76-103">referential integrity constraint</span></span>
<span data-ttu-id="bde76-104">*Ograniczenie integralności referencyjnej* w Entity Data Model (EDM) jest podobne do ograniczenia integralności referencyjnej w relacyjnej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="bde76-104">A *referential integrity constraint* in the Entity Data Model (EDM) is similar to a referential integrity constraint in a relational database.</span></span> <span data-ttu-id="bde76-105">W taki sam sposób, w jaki kolumna (lub kolumny) z tabeli bazy danych może odwoływać się do klucza podstawowego innej tabeli, [Właściwość](property.md) (lub właściwości) [typu jednostki](entity-type.md) może odwoływać się do [klucza jednostki](entity-key.md) innego typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="bde76-105">In the same way that a column (or columns) from a database table can reference the primary key of another table, a [property](property.md) (or properties) of an [entity type](entity-type.md) can reference the [entity key](entity-key.md) of another entity type.</span></span> <span data-ttu-id="bde76-106">Typ obiektu, do którego istnieje odwołanie, nazywa się *głównym końcem* ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="bde76-106">The entity type that is referenced is called the *principal end* of the constraint.</span></span> <span data-ttu-id="bde76-107">Typ jednostki, który odwołuje się do głównego końca, nazywa się *końcem zależnym* od ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="bde76-107">The entity type that references the principal end is called the *dependent end* of the constraint.</span></span>  
  
 <span data-ttu-id="bde76-108">Ograniczenie integralności referencyjnej jest zdefiniowane w ramach [skojarzenia](association-type.md) między dwoma typami jednostek.</span><span class="sxs-lookup"><span data-stu-id="bde76-108">A referential integrity constraint is defined as part of an [association](association-type.md) between two entity types.</span></span> <span data-ttu-id="bde76-109">Definicja ograniczenia integralności referencyjnej określa następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="bde76-109">The definition for a referential integrity constraint specifies the following information:</span></span>  
  
- <span data-ttu-id="bde76-110">Główny koniec ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="bde76-110">The principal end of the constraint.</span></span> <span data-ttu-id="bde76-111">(Typ jednostki, do której odwołuje się koniec zależny).</span><span class="sxs-lookup"><span data-stu-id="bde76-111">(An entity type whose entity key is referenced by the dependent end.)</span></span>  
  
- <span data-ttu-id="bde76-112">Klucz jednostki końca podmiotu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bde76-112">The entity key of the principal end.</span></span>  
  
- <span data-ttu-id="bde76-113">Zależne zakończenie ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="bde76-113">The dependent end of the constraint.</span></span> <span data-ttu-id="bde76-114">(Typ jednostki, który ma właściwość lub właściwości odwołujące się do klucza jednostki końcowego końca).</span><span class="sxs-lookup"><span data-stu-id="bde76-114">(An entity type that has a property or properties that reference the entity key of the principal end.)</span></span>  
  
- <span data-ttu-id="bde76-115">Właściwość odwołania lub właściwości elementu End zależnego.</span><span class="sxs-lookup"><span data-stu-id="bde76-115">The referencing property or properties of the dependent end.</span></span>  
  
 <span data-ttu-id="bde76-116">Ograniczenia więzów integralności w modelu EDM mają na celu zapewnienie, że poprawne skojarzenia zawsze istnieją.</span><span class="sxs-lookup"><span data-stu-id="bde76-116">The purpose of referential integrity constraints in the EDM is to ensure that valid associations always exist.</span></span> <span data-ttu-id="bde76-117">Aby uzyskać więcej informacji, zobacz [Właściwość klucza obcego](foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="bde76-117">For more information, see [foreign key property](foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bde76-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="bde76-118">Example</span></span>  
 <span data-ttu-id="bde76-119">Na poniższym diagramie przedstawiono model koncepcyjny z dwoma skojarzeniami: `WrittenBy` i `PublishedBy` .</span><span class="sxs-lookup"><span data-stu-id="bde76-119">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span> <span data-ttu-id="bde76-120">`Book`Typ jednostki ma właściwość, `PublisherId` która odwołuje się do klucza jednostki `Publisher` typu jednostki podczas definiowania ograniczenia integralności referencyjnej w `PublishedBy` skojarzeniu.</span><span class="sxs-lookup"><span data-stu-id="bde76-120">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="bde76-121">![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Przykład modelu ograniczeń referencyjnych")</span><span class="sxs-lookup"><span data-stu-id="bde76-121">![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="bde76-122">[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="bde76-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="bde76-123">Poniższy CSDL definiuje ograniczenie integralności referencyjnej względem `PublishedBy` skojarzenia pokazanego w modelu koncepcyjnym powyżej.</span><span class="sxs-lookup"><span data-stu-id="bde76-123">The following CSDL defines a referential integrity constraint on the `PublishedBy` association shown in the conceptual model above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="bde76-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bde76-124">See also</span></span>

- [<span data-ttu-id="bde76-125">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="bde76-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="bde76-126">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="bde76-126">Entity Data Model</span></span>](entity-data-model.md)
