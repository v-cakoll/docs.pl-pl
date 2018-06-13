---
title: Właściwość klucza obcego
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: 5a00c4d4cc469f5c816b8173843d283d63ccf308
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762653"
---
# <a name="foreign-key-property"></a>Właściwość klucza obcego
A *właściwości kluczy obcych* w modelu danych jednostki (EDM) jest typem pierwotnym [właściwości](../../../../docs/framework/data/adonet/property.md) (lub zestaw właściwości typu pierwotnego) na [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) zawierający [klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) innego typu jednostki.  
  
 Właściwości klucza obcego jest odpowiednikiem kolumny klucza obcego w relacyjnej bazie danych. W ten sam sposób, że kolumny klucza obcego są używane w relacyjnej bazie danych można utworzyć relacji między wierszy w tabelach, kluczy obcych w modelu koncepcyjnym są używane do ustanawiania [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) między typami jednostek. A [ograniczenia integralności referencyjnej](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) służy do definiowania skojarzenia między dwoma typami jednostek, gdy jeden z typów ma właściwości klucza obcego.  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`. `Book` Typ jednostki ma właściwości, `PublisherId`, który odwołuje się klucz `Publisher` typ jednostki po zdefiniowaniu ograniczenie integralności referencyjnej na `PublishedBy` skojarzenia.  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujący plik CSDL używa właściwości kluczy obcych `PublisherId` definiowania ograniczenie integralności referencyjnej w `PublishedBy` skojarzenia wyświetlany w modelu koncepcyjnym przedstawionych powyżej.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
