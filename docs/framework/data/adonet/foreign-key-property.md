---
title: Właściwość klucza obcego
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: a33d60e28c7c4e5a90199437fc95a83b5a304b06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746612"
---
# <a name="foreign-key-property"></a>Właściwość klucza obcego
A *właściwość klucza obcego* w Entity Data Model (EDM) jest typem pierwotnym [właściwość](../../../../docs/framework/data/adonet/property.md) (lub zestaw właściwości typu pierwotnego) na [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) zawierający [klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) innego typu jednostki.  
  
 Właściwość klucza obcego jest analogiczne do kolumny klucza obcego w relacyjnej bazie danych. W ten sam sposób, że kolumny klucza obcego są używane w relacyjnej bazie danych do tworzenia relacji między wierszy w tabelach, właściwości klucza obcego w modelu koncepcyjnym są używane do ustanawiania [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) między typami encji. A [ograniczenia integralności referencyjnej](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) służy do definiowania skojarzenie między dwoma typami encji, gdy jeden z typów ma właściwość klucza obcego.  
  
## <a name="example"></a>Przykład  
 Poniższy diagram przedstawia modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`. `Book` Typ jednostki ma właściwość, `PublisherId`, który odwołuje się klucz `Publisher` typu jednostki podczas definiowania ograniczenia integralności referencyjnej w `PublishedBy` skojarzenia.  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujące CSDL używa właściwości klucza obcego `PublisherId` definiowania ograniczenia integralności referencyjnej w `PublishedBy` skojarzenia wyświetlane w modelu koncepcyjnym przedstawionych powyżej.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Zobacz także
- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
