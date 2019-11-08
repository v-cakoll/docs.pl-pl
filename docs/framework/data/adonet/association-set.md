---
title: zestaw skojarzeń
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: e279322f9e950cd4359db8c6dce39bfc46d188f6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732377"
---
# <a name="association-set"></a>zestaw skojarzeń
*Zestaw skojarzeń* to logiczny kontener dla wystąpień [skojarzeń](association-type.md) tego samego typu. Zestaw skojarzeń nie jest konstrukcją modelowania danych; oznacza to, że nie opisuje struktury danych lub relacji. Zamiast tego zestaw skojarzeń zawiera konstrukcję dla środowiska hostingu lub magazynu (na przykład środowisko uruchomieniowe języka wspólnego lub SQL Server Database) w celu grupowania wystąpień skojarzeń, aby można je było mapować do magazynu danych.  
  
 Zestaw skojarzeń jest zdefiniowany w [kontenerze jednostek](entity-container.md), który jest logicznym grupowaniem [zestawów jednostek](entity-set.md) i zestawów skojarzeń.  
  
 Definicja zestawu skojarzenia zawiera następujące informacje:  
  
- Nazwa zestawu skojarzeń. Potrzeb  
  
- Skojarzenie, którego będzie zawierać wystąpienia. Potrzeb  
  
- Dwa [punkty końcowe zestawu skojarzenia](association-set-end.md).  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z dwoma skojarzeniami: `PublishedBy`i `WrittenBy`. Chociaż informacje o zestawach skojarzeń nie są przekazywane na diagramie, na następnym diagramie przedstawiono przykład zestawów skojarzeń i zestawów jednostek opartych na tym modelu.  
  
 ![Przykładowy model z trzema typami jednostek](./media/association-set/example-model-three-entity-types.gif)  
  
 Poniższy przykład przedstawia zestaw skojarzeń (`PublishedBy`) i dwa zestawy jednostek (`Books` i `Publishers`) w oparciu o model koncepcyjny przedstawiony powyżej. Usługa BI w zestawie jednostek `Books` reprezentuje wystąpienie typu jednostki `Book` w czasie wykonywania. Podobnie PJ reprezentuje wystąpienie `Publisher` w zestawie jednostek `Publishers`. BiPj reprezentuje wystąpienie skojarzenia `PublishedBy` w zestawie skojarzeń `PublishedBy`.  
  
 ![Zrzut ekranu pokazujący przykład zestawu.](./media/association-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych. Następujący CSDL definiuje kontener jednostek z jednym zestawem skojarzenia dla każdego skojarzenia na powyższym diagramie. Należy zauważyć, że nazwa i skojarzenie dla każdego zestawu skojarzeń są zdefiniowane przy użyciu atrybutów XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Istnieje możliwość zdefiniowania wielu zestawów skojarzeń na każde skojarzenie, o ile żadne z dwóch zestawów skojarzeń nie współdzieli [końca zestawu skojarzenia](association-set-end.md). Poniższy identyfikator CSDL definiuje kontener jednostek z dwoma zestawami skojarzenia dla skojarzenia `WrittenBy`. Zauważ, że dla `Book` i `Author` typy jednostek zostały zdefiniowane wiele zestawów jednostek i że żaden z nich nie udostępnia końcowego zestawu skojarzenia.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
- [właściwość klucza obcego](foreign-key-property.md)
