---
title: ograniczenie integralności referencyjnej
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: 7d3304393ef4e97887d9b8afec94ed265e38eaf0
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679115"
---
# <a name="referential-integrity-constraint"></a>ograniczenie integralności referencyjnej
A *ograniczenia integralności referencyjnej* w Entity Data Model (EDM) jest podobny do ograniczenia integralności referencyjnej w relacyjnej bazie danych. W ten sam sposób, w kolumnie (lub kolumny) z tabeli bazy danych odwołać się do klucza podstawowego z innej tabeli [właściwość](../../../../docs/framework/data/adonet/property.md) (lub właściwości) z [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) może odwoływać się [klucza jednostki ](../../../../docs/framework/data/adonet/entity-key.md) innego typu jednostki. Typ jednostki, do którego istnieje odwołanie jest wywoływana *jednostki zakończenia* ograniczenia. Typ jednostki, który odwołuje się do zakończenia podmiotu zabezpieczeń jest wywoływana *zależne zakończenia* ograniczenia.  
  
 Ograniczenie integralności referencyjnej jest zdefiniowany jako część [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) między dwoma typami encji. Definicja dla ograniczenia integralności referencyjnej określa następujące informacje:  
  
-   Główny koniec tego ograniczenia. (Typ jednostki którego klucz jednostki odwołuje się do zakończenia zależnego.)  
  
-   Klucz elementu end podmiotu zabezpieczeń.  
  
-   Zależne zakończenia tego ograniczenia. (Typ jednostki obsługiwanej przez właściwość lub właściwości odwołujące się do klucza jednostki głównej zakończenia.)  
  
-   Odwołujący się właściwości lub właściwości końca zależnych.  
  
 Celem ograniczenia integralności referencyjnej w EDM jest zapewnienie, prawidłowy skojarzenia zawsze istnieje. Aby uzyskać więcej informacji, zobacz [właściwość klucza obcego](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## <a name="example"></a>Przykład  
 Poniższy diagram przedstawia modelu koncepcyjnego z dwóch skojarzeń: `WrittenBy` i `PublishedBy`. `Book` Typ jednostki ma właściwość, `PublisherId`, który odwołuje się klucz `Publisher` typu jednostki podczas definiowania ograniczenia integralności referencyjnej w `PublishedBy` skojarzenia.  
  
 ![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "przykładowy model ograniczenie referencyjne")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujące CSDL definiuje ograniczenia integralności referencyjnej w `PublishedBy` skojarzenia wyświetlane w modelu koncepcyjnym powyżej.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Zobacz także
- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
