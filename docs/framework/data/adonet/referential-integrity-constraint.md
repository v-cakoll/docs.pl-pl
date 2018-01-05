---
title: "ograniczenie integralności referencyjnej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 232098a4940e223fd8553eefa4964777b1695c5b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="referential-integrity-constraint"></a><span data-ttu-id="4e76e-102">ograniczenie integralności referencyjnej</span><span class="sxs-lookup"><span data-stu-id="4e76e-102">referential integrity constraint</span></span>
<span data-ttu-id="4e76e-103">A *ograniczenia integralności referencyjnej* w modelu danych jednostki (EDM) jest podobny do ograniczenia integralności referencyjnej w relacyjnej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="4e76e-103">A *referential integrity constraint* in the Entity Data Model (EDM) is similar to a referential integrity constraint in a relational database.</span></span> <span data-ttu-id="4e76e-104">W ten sam sposób, że kolumna (lub kolumny) z tabeli bazy danych może odwoływać się klucz podstawowy innej tabeli [właściwości](../../../../docs/framework/data/adonet/property.md) (lub właściwości) z [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) może odwoływać się [klucz jednostki ](../../../../docs/framework/data/adonet/entity-key.md) innego typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="4e76e-104">In the same way that a column (or columns) from a database table can reference the primary key of another table, a [property](../../../../docs/framework/data/adonet/property.md) (or properties) of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) can reference the [entity key](../../../../docs/framework/data/adonet/entity-key.md) of another entity type.</span></span> <span data-ttu-id="4e76e-105">Typ jednostki, do którego odwołuje się jest wywoływana *główny koniec* ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="4e76e-105">The entity type that is referenced is called the *principal end* of the constraint.</span></span> <span data-ttu-id="4e76e-106">Typów jednostek, które odwołuje się do zakończenia podmiotu zabezpieczeń jest nazywany *zależnego końca* ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="4e76e-106">The entity type that references the principal end is called the *dependent end* of the constraint.</span></span>  
  
 <span data-ttu-id="4e76e-107">Ograniczenie integralności referencyjnej jest definiowane jako część [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) między dwoma typami jednostek.</span><span class="sxs-lookup"><span data-stu-id="4e76e-107">A referential integrity constraint is defined as part of an [association](../../../../docs/framework/data/adonet/association-type.md) between two entity types.</span></span> <span data-ttu-id="4e76e-108">Definicja dla ograniczenia integralności referencyjnej określa następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="4e76e-108">The definition for a referential integrity constraint specifies the following information:</span></span>  
  
-   <span data-ttu-id="4e76e-109">Głównego końca ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="4e76e-109">The principal end of the constraint.</span></span> <span data-ttu-id="4e76e-110">(Typ jednostki którego klucz jednostki odwołuje się do niego zależnego końca.)</span><span class="sxs-lookup"><span data-stu-id="4e76e-110">(An entity type whose entity key is referenced by the dependent end.)</span></span>  
  
-   <span data-ttu-id="4e76e-111">Klucz główny końca.</span><span class="sxs-lookup"><span data-stu-id="4e76e-111">The entity key of the principal end.</span></span>  
  
-   <span data-ttu-id="4e76e-112">Zależnego końca ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="4e76e-112">The dependent end of the constraint.</span></span> <span data-ttu-id="4e76e-113">(Typ jednostki, który ma właściwość lub właściwości, które odwołują się klucz główny koniec.)</span><span class="sxs-lookup"><span data-stu-id="4e76e-113">(An entity type that has a property or properties that reference the entity key of the principal end.)</span></span>  
  
-   <span data-ttu-id="4e76e-114">Odwołaniem do właściwości lub właściwości zależnego końca.</span><span class="sxs-lookup"><span data-stu-id="4e76e-114">The referencing property or properties of the dependent end.</span></span>  
  
 <span data-ttu-id="4e76e-115">Celem ograniczenia integralności referencyjnej w modelu EDM jest zapewnienie, prawidłowy skojarzenia zawsze istnieje.</span><span class="sxs-lookup"><span data-stu-id="4e76e-115">The purpose of referential integrity constraints in the EDM is to ensure that valid associations always exist.</span></span> <span data-ttu-id="4e76e-116">Aby uzyskać więcej informacji, zobacz [właściwości kluczy obcych](../../../../docs/framework/data/adonet/foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="4e76e-116">For more information, see [foreign key property](../../../../docs/framework/data/adonet/foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e76e-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="4e76e-117">Example</span></span>  
 <span data-ttu-id="4e76e-118">Na poniższym diagramie przedstawiono modelu koncepcyjnego z dwóch skojarzenia: `WrittenBy` i `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="4e76e-118">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span> <span data-ttu-id="4e76e-119">`Book` Typ jednostki ma właściwości, `PublisherId`, który odwołuje się klucz `Publisher` typ jednostki po zdefiniowaniu ograniczenie integralności referencyjnej na `PublishedBy` skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="4e76e-119">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="4e76e-120">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span><span class="sxs-lookup"><span data-stu-id="4e76e-120">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span></span>  
  
 <span data-ttu-id="4e76e-121">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="4e76e-121">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="4e76e-122">Następujący plik CSDL definiuje ograniczenia integralności referencyjnej w `PublishedBy` skojarzenia wyświetlany w modelu koncepcyjnym powyżej.</span><span class="sxs-lookup"><span data-stu-id="4e76e-122">The following CSDL defines a referential integrity constraint on the `PublishedBy` association shown in the conceptual model above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="4e76e-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e76e-123">See Also</span></span>  
 [<span data-ttu-id="4e76e-124">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="4e76e-124">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="4e76e-125">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="4e76e-125">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
