---
title: ograniczenie integralności referencyjnej
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: 28880c7085f8b4e3dd2e51b5633c1f0e2a984a4b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794443"
---
# <a name="referential-integrity-constraint"></a>ograniczenie integralności referencyjnej
*Ograniczenie integralności referencyjnej* w Entity Data Model (EDM) jest podobne do ograniczenia integralności referencyjnej w relacyjnej bazie danych. W taki sam sposób, w jaki kolumna (lub kolumny) z tabeli bazy danych może odwoływać się do klucza podstawowego innej tabeli, [Właściwość](property.md) (lub właściwości) [typu jednostki](entity-type.md) może odwoływać się do [klucza jednostki](entity-key.md) innego typu jednostki. Typ obiektu, do którego istnieje odwołanie, nazywa się *głównym końcem* ograniczenia. Typ jednostki, który odwołuje się do głównego końca, nazywa się *końcem zależnym* od ograniczenia.  
  
 Ograniczenie integralności referencyjnej jest zdefiniowane w ramach [skojarzenia](association-type.md) między dwoma typami jednostek. Definicja ograniczenia integralności referencyjnej określa następujące informacje:  
  
- Główny koniec ograniczenia. (Typ jednostki, do której odwołuje się koniec zależny).  
  
- Klucz jednostki końca podmiotu zabezpieczeń.  
  
- Zależne zakończenie ograniczenia. (Typ jednostki, który ma właściwość lub właściwości odwołujące się do klucza jednostki końcowego końca).  
  
- Właściwość odwołania lub właściwości elementu End zależnego.  
  
 Ograniczenia więzów integralności w modelu EDM mają na celu zapewnienie, że poprawne skojarzenia zawsze istnieją. Aby uzyskać więcej informacji, zobacz [Właściwość klucza obcego](foreign-key-property.md).  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z dwoma skojarzeniami: `WrittenBy` i `PublishedBy`. Typ jednostki ma właściwość, `PublisherId`która odwołuje `Publisher` się do klucza jednostki typu jednostki podczas definiowania ograniczenia integralności referencyjnej w `PublishedBy` skojarzeniu. `Book`  
  
 ![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Przykład modelu ograniczeń referencyjnych")  
  
 [ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Poniższy CSDL definiuje ograniczenie integralności referencyjnej względem `PublishedBy` skojarzenia pokazanego w modelu koncepcyjnym powyżej.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
