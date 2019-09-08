---
title: zestaw skojarzeń
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: 43ab6cf9f1ee8cb971810add6b9a89467726f3e2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785030"
---
# <a name="association-set"></a>zestaw skojarzeń
*Zestaw skojarzeń* to logiczny kontener dla wystąpień [skojarzeń](association-type.md) tego samego typu. Zestaw skojarzeń nie jest konstrukcją modelowania danych; oznacza to, że nie opisuje struktury danych lub relacji. Zamiast tego zestaw skojarzeń zawiera konstrukcję dla środowiska hostingu lub magazynu (na przykład środowisko uruchomieniowe języka wspólnego lub SQL Server Database) w celu grupowania wystąpień skojarzeń, aby można je było mapować do magazynu danych.  
  
 Zestaw skojarzeń jest zdefiniowany w [kontenerze jednostek](entity-container.md), który jest logicznym grupowaniem [zestawów jednostek](entity-set.md) i zestawów skojarzeń.  
  
 Definicja zestawu skojarzenia zawiera następujące informacje:  
  
- Nazwa zestawu skojarzeń. Potrzeb  
  
- Skojarzenie, którego będzie zawierać wystąpienia. Potrzeb  
  
- Dwa [punkty końcowe zestawu skojarzenia](association-set-end.md).  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z dwoma skojarzeniami: `PublishedBy`i. `WrittenBy` Chociaż informacje o zestawach skojarzeń nie są przekazywane na diagramie, na następnym diagramie przedstawiono przykład zestawów skojarzeń i zestawów jednostek opartych na tym modelu.  
  
 ![Przykładowy model z trzema typami jednostek](./media/association-set/example-model-three-entity-types.gif)  
  
 Poniższy przykład przedstawia zestaw skojarzeń (`PublishedBy`) i dwa zestawy jednostek (`Books` i `Publishers`) na podstawie modelu koncepcyjnego pokazanego powyżej. Usługa BI w `Books` zestawie jednostek reprezentuje wystąpienie `Book` typu jednostki w czasie wykonywania. Podobnie PJ reprezentuje `Publisher` wystąpienie `Publishers` w zestawie jednostek. BiPj reprezentuje wystąpienie `PublishedBy` skojarzenia `PublishedBy` w zestawie skojarzeń.  
  
 ![Zrzut ekranu pokazujący przykład zestawu.](./media/association-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujący CSDL definiuje kontener jednostek z jednym zestawem skojarzenia dla każdego skojarzenia na powyższym diagramie. Należy zauważyć, że nazwa i skojarzenie dla każdego zestawu skojarzeń są zdefiniowane przy użyciu atrybutów XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Istnieje możliwość zdefiniowania wielu zestawów skojarzeń na każde skojarzenie, o ile żadne z dwóch zestawów skojarzeń nie współdzieli [końca zestawu skojarzenia](association-set-end.md). Poniższy CSDL definiuje kontener jednostek z dwoma zestawami skojarzeń dla `WrittenBy` skojarzenia. Zauważ, że zdefiniowano wiele zestawów jednostek dla `Book` obiektów i `Author` i że żaden z zestawów skojarzeń nie udostępnia końcowego zestawu skojarzenia.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
- [właściwość klucza obcego](foreign-key-property.md)
