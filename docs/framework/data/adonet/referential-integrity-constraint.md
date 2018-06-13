---
title: ograniczenie integralności referencyjnej
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: a4d63e07da0c75b8a0369933fccfc0cc66fcc40b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352642"
---
# <a name="referential-integrity-constraint"></a>ograniczenie integralności referencyjnej
A *ograniczenia integralności referencyjnej* w modelu danych jednostki (EDM) jest podobny do ograniczenia integralności referencyjnej w relacyjnej bazie danych. W ten sam sposób, że kolumna (lub kolumny) z tabeli bazy danych może odwoływać się klucz podstawowy innej tabeli [właściwości](../../../../docs/framework/data/adonet/property.md) (lub właściwości) z [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) może odwoływać się [klucz jednostki ](../../../../docs/framework/data/adonet/entity-key.md) innego typu jednostki. Typ jednostki, do którego odwołuje się jest wywoływana *główny koniec* ograniczenia. Typów jednostek, które odwołuje się do zakończenia podmiotu zabezpieczeń jest nazywany *zależnego końca* ograniczenia.  
  
 Ograniczenie integralności referencyjnej jest definiowane jako część [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) między dwoma typami jednostek. Definicja dla ograniczenia integralności referencyjnej określa następujące informacje:  
  
-   Głównego końca ograniczenia. (Typ jednostki którego klucz jednostki odwołuje się do niego zależnego końca.)  
  
-   Klucz główny końca.  
  
-   Zależnego końca ograniczenia. (Typ jednostki, który ma właściwość lub właściwości, które odwołują się klucz główny koniec.)  
  
-   Odwołaniem do właściwości lub właściwości zależnego końca.  
  
 Celem ograniczenia integralności referencyjnej w modelu EDM jest zapewnienie, prawidłowy skojarzenia zawsze istnieje. Aby uzyskać więcej informacji, zobacz [właściwości kluczy obcych](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z dwóch skojarzenia: `WrittenBy` i `PublishedBy`. `Book` Typ jednostki ma właściwości, `PublisherId`, który odwołuje się klucz `Publisher` typ jednostki po zdefiniowaniu ograniczenie integralności referencyjnej na `PublishedBy` skojarzenia.  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujący plik CSDL definiuje ograniczenia integralności referencyjnej w `PublishedBy` skojarzenia wyświetlany w modelu koncepcyjnym powyżej.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
