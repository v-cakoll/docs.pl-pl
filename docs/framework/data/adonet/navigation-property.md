---
title: Właściwość nawigacji
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: 149aefe84c9d04fab1786b99c2ac8c5060bccd87
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="navigation-property"></a>Właściwość nawigacji
A *właściwość nawigacji* jest opcjonalna właściwość na [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) umożliwiająca nawigacji z jednego [zakończenia](../../../../docs/framework/data/adonet/association-end.md) z [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) do Data zakończenia. W odróżnieniu od innych [właściwości](../../../../docs/framework/data/adonet/property.md), właściwości nawigacji nie zawierają danych.  
  
 Definicja właściwości nawigacji obejmuje następujące funkcje:  
  
-   Nazwa. (Wymagane)  
  
-   Skojarzenie prowadzącego go. (Wymagane)  
  
-   Punkty końcowe skojarzenia, który nawiguje go. (Wymagane)  
  
 Należy pamiętać, że właściwości nawigacji są opcjonalne na obu typów jednostek na końcu skojarzenia. Definiuje właściwości nawigacji na jeden typ jednostki na końcu skojarzenia, nie trzeba zdefiniować właściwości nawigacji dla typu jednostki na drugim końcu skojarzenia.  
  
 Typ danych właściwości nawigacji jest określany przez [liczebność](../../../../docs/framework/data/adonet/association-end-multiplicity.md) jego zdalnego [końca skojarzenia](../../../../docs/framework/data/adonet/association-end.md). Na przykład, załóżmy, że właściwość nawigacji, `OrdersNavProp`, istnieje na `Customer` typu jednostki i przechodzi jeden do wielu skojarzenie `Customer` i `Order`. Punkt końcowy zdalnego dla właściwości nawigacji ma liczebność wielu (*), jego typ danych to kolekcja (z `Order`). Podobnie, jeśli właściwość nawigacji, `CustomerNavProp`, istnieje na `Order` typu jednostki, typu danych będzie `Customer`, ponieważ liczebność końca zdalnego jest jeden (1).  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`. Właściwości nawigacji `Publisher` i `Authors`, są zdefiniowane w typie jednostek książki. Właściwość nawigacji `Books` jest zdefiniowany w obu typie jednostek wydawcy i `Author` typu jednostki.  
  
 ![Modelu z właściwości nawigacji](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Definiuje następujące CSDL `Book` typu jednostki pokazano na powyższym diagramie:  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Należy pamiętać, że atrybuty XML są używane do komunikacji informacje niezbędne do definiowania właściwości nawigacji: atrybut `Name` zawiera nazwę właściwości, `Relationship` zawiera nazwę skojarzenia przechodzi on, i `FromRole` i `ToRole` zawierają punkty końcowe skojarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
