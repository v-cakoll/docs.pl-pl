---
title: punkt końcowy zestawu skojarzeń
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: f7ec1ca6fcdf299b9fcfc78f299ea4c6c5267cd3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738617"
---
# <a name="association-set-end"></a>punkt końcowy zestawu skojarzeń
*Koniec zestawu skojarzeń* identyfikuje [Typ jednostki](entity-type.md) i [jednostkę ustawioną](entity-set.md) na końcu [zestawu skojarzenia](association-set.md). Zakończenia zestawu skojarzeń są definiowane jako część zestawu skojarzenia; zestaw skojarzeń musi mieć dokładnie dwa punkty końcowe zestawu skojarzenia.  
  
 Definicja końcowa zestawu skojarzeń zawiera następujące informacje:  
  
- Jeden z typów jednostek należących do zestawu skojarzeń. Potrzeb  
  
- Zestaw jednostek dla typu jednostki, który jest powiązany z zestawem skojarzeń. Potrzeb  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z dwoma skojarzeniami: `WrittenBy` i `PublishedBy`.  
  
 ![Przykładowy model z trzema typami jednostek](./media/association-set-end/example-model-three-entity-types.gif)  
  
 Na poniższym diagramie przedstawiono zestaw skojarzeń (`PublishedBy`) i dwa zestawy jednostek (`Books` i `Publishers`) w oparciu o model koncepcyjny przedstawiony powyżej. Zestaw skojarzenia zostaje zakończony, `Books` i `Publishers` zestawy jednostek. Usługa BI w zestawie jednostek `Books` reprezentuje wystąpienie typu jednostki `Book` w czasie wykonywania. Podobnie PJ reprezentuje wystąpienie `Publisher` w zestawie jednostek `Publishers`. BiPj reprezentuje wystąpienie skojarzenia `PublishedBy` w zestawie skojarzeń `PublishedBy`.  
  
 ![Zrzut ekranu pokazujący przykład zestawu.](./media/association-set-end/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) używa języka DSL o nazwie koncepcyjny schemat definicji schematu ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych. Następujący CSDL definiuje kontener jednostek z jednym zestawem skojarzenia dla każdego skojarzenia na powyższym diagramie. Należy zauważyć, że końcówki zestawu skojarzeń są zdefiniowane jako część każdej definicji zestawu skojarzeń.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
