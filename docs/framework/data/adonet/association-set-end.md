---
title: punkt końcowy zestawu skojarzeń
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 7b6c646592c1878ea30396d98b4976dc8fa0be12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769593"
---
# <a name="association-set-end"></a>punkt końcowy zestawu skojarzeń
*Punkt końcowy zestawu skojarzeń* identyfikuje [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) i [zestaw jednostek](../../../../docs/framework/data/adonet/entity-set.md) na końcu [zestaw skojarzeń](../../../../docs/framework/data/adonet/association-set.md). Skojarzenie zestawu są zdefiniowane jako część zestawu skojarzeń; zestaw skojarzeń musi mieć dokładnie dwa skojarzenie zestawu.  
  
 Definicję końcowy zestawu skojarzeń zawiera następujące informacje:  
  
- Ustaw jeden z typów jednostek zaangażowanych w skojarzeniu. (Wymagane)  
  
- Zestaw jednostek dla typu jednostki związane z zestaw skojarzeń. (Wymagane)  
  
## <a name="example"></a>Przykład  
 Poniższy diagram przedstawia modelu koncepcyjnego z dwóch skojarzeń: `WrittenBy` i `PublishedBy`.  
  
 ![Przykładowy model przy użyciu trzech typów jednostek](./media/association-set-end/example-model-three-entity-types.gif)  
  
 Na poniższym diagramie przedstawiono zestaw skojarzeń (`PublishedBy`) i dwa zestawy jednostek (`Books` i `Publishers`) oparte na modelu koncepcyjnego przedstawionych powyżej. Skojarzenie zestawu są `Books` i `Publishers` zestawy jednostek. Analizy biznesowej w `Books` zestaw jednostek reprezentuje wystąpienie `Book` typu jednostki w czasie wykonywania. Podobnie, reprezentuje Pj `Publisher` wystąpienia w `Publishers` zestawu jednostek. BiPj reprezentuje wystąpienie `PublishedBy` skojarzenia w `PublishedBy` zestaw skojarzeń.  
  
 ![Zrzut ekranu przedstawia przykład zestawów.](./media/association-set-end/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa o nazwie język definicji schematu koncepcyjnego języka DSL ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujące CSDL definiuje kontener jednostek z jednej skojarzenia dla każdego skojarzenia na powyższym diagramie. Należy pamiętać, że zestaw końcowych są zdefiniowane jako część każdej definicji zestawu skojarzeń.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
