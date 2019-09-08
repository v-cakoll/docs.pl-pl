---
title: właściwość klucza obcego
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: e2f41c2db9aea26c7954a99ebf3f40b03e8df735
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795028"
---
# <a name="foreign-key-property"></a>właściwość klucza obcego
*Właściwość klucza obcego* w Entity Data Model (EDM) jest [właściwością](property.md) typu pierwotnego (lub zestawem właściwości typu pierwotnego) dla [typu jednostki](entity-type.md) , który zawiera [klucz jednostki](entity-key.md) innego typu jednostki.  
  
 Właściwość klucza obcego jest analogiczna do kolumny klucza obcego w relacyjnej bazie danych. W taki sam sposób, w jaki kolumny klucza obcego są używane w relacyjnej bazie danych do tworzenia relacji między wierszami w tabelach, właściwości klucza obcego w modelu koncepcyjnym są używane do ustanawiania [skojarzeń](association-type.md) między typami jednostek. [Ograniczenie integralności referencyjnej](referential-integrity-constraint.md) służy do definiowania skojarzenia między dwoma typami jednostek, gdy jeden z typów ma właściwość klucza obcego.  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`. Typ jednostki ma właściwość, `PublisherId`która odwołuje `Publisher` się do klucza jednostki typu jednostki podczas definiowania ograniczenia integralności referencyjnej w `PublishedBy` skojarzeniu. `Book`  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Przykład modelu ograniczeń referencyjnych")  
  
 [ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Poniższy CSDL używa właściwości `PublisherId` klucza obcego do zdefiniowania ograniczenia integralności referencyjnej `PublishedBy` na skojarzeniu pokazanym powyżej.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
