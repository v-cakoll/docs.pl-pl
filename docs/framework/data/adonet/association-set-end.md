---
title: Konfigurowanie skojarzenia
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 440cfdee4581496d9d131fbaf3d1796f38931532
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="association-set-end"></a>Konfigurowanie skojarzenia
*Konfigurowanie skojarzenia* identyfikuje [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) i [zestaw jednostek](../../../../docs/framework/data/adonet/entity-set.md) na końcu [zestawu skojarzeń](../../../../docs/framework/data/adonet/association-set.md). Punkty końcowe skojarzenia zestawu są definiowane jako część zestawu skojarzeń; zestaw skojarzenia musi mieć dokładnie dwa skojarzenie zestawu.  
  
 Koniec definicji zestawu skojarzenia zawiera następujące informacje:  
  
-   Jeden z typów jednostek objętego skojarzenie ustawiony. (Wymagane)  
  
-   Zestaw jednostek dla typu jednostki objętego zestawu skojarzeń. (Wymagane)  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z dwóch skojarzenia: `WrittenBy` i `PublishedBy`.  
  
 ![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Na poniższym diagramie przedstawiono zestawu skojarzeń (`PublishedBy`) i dwa zestawy jednostek (`Books` i `Publishers`) oparte na modelu koncepcyjnego przedstawionych powyżej. Skojarzenie zestawu są `Books` i `Publishers` zestawów jednostek. Analizy biznesowej w `Books` zestaw jednostek reprezentuje wystąpienie `Book` typu jednostki w czasie wykonywania. Podobnie, uzyskać reprezentuje `Publisher` wystąpienia w `Publishers` zestawu jednostek. BiPj reprezentuje wystąpienie `PublishedBy` skojarzenia w `PublishedBy` zestawu skojarzeń.  
  
 ![Ustawia przykład](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa DSL, nazywany języka definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujący plik CSDL definiuje kontenera jednostek z jednego zestawu dla każdego skojarzenia na powyższym diagramie skojarzeń. Należy pamiętać, że skojarzenie zestawu są zdefiniowane jako część każdego definicji zestawu skojarzeń.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
