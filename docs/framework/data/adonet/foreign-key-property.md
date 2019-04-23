---
title: właściwość klucza obcego
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: 74117b30ca54f7c57bd970003fc6f5dcc54d553f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218020"
---
# <a name="foreign-key-property"></a>właściwość klucza obcego
A *właściwość klucza obcego* w Entity Data Model (EDM) jest typem pierwotnym [właściwość](../../../../docs/framework/data/adonet/property.md) (lub zestaw właściwości typu pierwotnego) na [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) zawierający [klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) innego typu jednostki.  
  
 Właściwość klucza obcego jest analogiczne do kolumny klucza obcego w relacyjnej bazie danych. W ten sam sposób, że kolumny klucza obcego są używane w relacyjnej bazie danych do tworzenia relacji między wierszy w tabelach, właściwości klucza obcego w modelu koncepcyjnym są używane do ustanawiania [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) między typami encji. A [ograniczenia integralności referencyjnej](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) służy do definiowania skojarzenie między dwoma typami encji, gdy jeden z typów ma właściwość klucza obcego.  
  
## <a name="example"></a>Przykład  
 Poniższy diagram przedstawia modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`. `Book` Typ jednostki ma właściwość, `PublisherId`, który odwołuje się klucz `Publisher` typu jednostki podczas definiowania ograniczenia integralności referencyjnej w `PublishedBy` skojarzenia.  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "przykładowy model ograniczenie referencyjne")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujące CSDL używa właściwości klucza obcego `PublisherId` definiowania ograniczenia integralności referencyjnej w `PublishedBy` skojarzenia wyświetlane w modelu koncepcyjnym przedstawionych powyżej.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
