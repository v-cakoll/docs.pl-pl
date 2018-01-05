---
title: "Właściwość klucza obcego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 91d06e50a2c64c649ff35352f5b4a41c7417efdf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="foreign-key-property"></a><span data-ttu-id="c4a38-102">Właściwość klucza obcego</span><span class="sxs-lookup"><span data-stu-id="c4a38-102">foreign key property</span></span>
<span data-ttu-id="c4a38-103">A *właściwości kluczy obcych* w modelu danych jednostki (EDM) jest typem pierwotnym [właściwości](../../../../docs/framework/data/adonet/property.md) (lub zestaw właściwości typu pierwotnego) na [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) zawierający [klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) innego typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="c4a38-103">A *foreign key property* in the Entity Data Model (EDM) is a primitive type [property](../../../../docs/framework/data/adonet/property.md) (or a set of primitive type properties) on an [entity type](../../../../docs/framework/data/adonet/entity-type.md) that contains the [entity key](../../../../docs/framework/data/adonet/entity-key.md) of another entity type.</span></span>  
  
 <span data-ttu-id="c4a38-104">Właściwości klucza obcego jest odpowiednikiem kolumny klucza obcego w relacyjnej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="c4a38-104">A foreign key property is analogous to a foreign key column in a relational database.</span></span> <span data-ttu-id="c4a38-105">W ten sam sposób, że kolumny klucza obcego są używane w relacyjnej bazie danych można utworzyć relacji między wierszy w tabelach, kluczy obcych w modelu koncepcyjnym są używane do ustanawiania [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) między typami jednostek.</span><span class="sxs-lookup"><span data-stu-id="c4a38-105">In the same way that foreign key columns are used in a relational database to create relationships between rows in tables, foreign key properties in a conceptual model are used to establish [associations](../../../../docs/framework/data/adonet/association-type.md) between entity types.</span></span> <span data-ttu-id="c4a38-106">A [ograniczenia integralności referencyjnej](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) służy do definiowania skojarzenia między dwoma typami jednostek, gdy jeden z typów ma właściwości klucza obcego.</span><span class="sxs-lookup"><span data-stu-id="c4a38-106">A [referential integrity constraint](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) is used to define an association between two entity types when one of the types has a foreign key property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4a38-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4a38-107">Example</span></span>  
 <span data-ttu-id="c4a38-108">Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`.</span><span class="sxs-lookup"><span data-stu-id="c4a38-108">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="c4a38-109">`Book` Typ jednostki ma właściwości, `PublisherId`, który odwołuje się klucz `Publisher` typ jednostki po zdefiniowaniu ograniczenie integralności referencyjnej na `PublishedBy` skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="c4a38-109">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="c4a38-110">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span><span class="sxs-lookup"><span data-stu-id="c4a38-110">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span></span>  
  
 <span data-ttu-id="c4a38-111">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="c4a38-111">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="c4a38-112">Następujący plik CSDL używa właściwości kluczy obcych `PublisherId` definiowania ograniczenie integralności referencyjnej w `PublishedBy` skojarzenia wyświetlany w modelu koncepcyjnym przedstawionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="c4a38-112">The following CSDL uses the foreign key property `PublisherId` to define a referential integrity constraint on the `PublishedBy` association shown in the conceptual model shown above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="c4a38-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4a38-113">See Also</span></span>  
 [<span data-ttu-id="c4a38-114">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="c4a38-114">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="c4a38-115">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="c4a38-115">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
