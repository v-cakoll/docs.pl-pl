---
title: zestaw skojarzeń
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: b7ded35986d27dedccbc3846f8791974bb225398
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592569"
---
# <a name="association-set"></a>zestaw skojarzeń
*Zestaw skojarzeń* to logiczny kontener przeznaczony do [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) wystąpień tego samego typu. Zestaw skojarzeń nie jest konstrukcja; modelowania danych oznacza to, że nie opisano strukturę danych lub relacje. Zamiast tego zestaw skojarzeń zapewnia konstrukcję w środowisku hostingu lub magazynu (np. środowisko uruchomieniowe języka wspólnego lub bazą danych programu SQL Server) do wystąpień skojarzenia grupy mogą być mapowane do magazynu danych.  
  
 Zestaw skojarzeń jest zdefiniowana w [kontener jednostek](../../../../docs/framework/data/adonet/entity-container.md), która jest logicznym grupowaniem [zestawy jednostek](../../../../docs/framework/data/adonet/entity-set.md) i zestawów skojarzeń.  
  
 Definicja zestawu skojarzeń zawiera następujące informacje:  
  
- Nazwa zestawu skojarzenia. (Wymagane)  
  
- Skojarzenia, które będzie zawierać wystąpień. (Wymagane)  
  
- Dwa [kończy się zestawu skojarzeń](../../../../docs/framework/data/adonet/association-set-end.md).  
  
## <a name="example"></a>Przykład  
 Poniższy diagram przedstawia modelu koncepcyjnego z dwóch skojarzeń: `PublishedBy`, i `WrittenBy`. Mimo że informacji na temat zestawów skojarzenie nie jest przekazywany w diagramie, następny diagram pokazuje przykład zestawów skojarzeń i zestawy jednostek, w oparciu o ten model.  
  
 ![Przykładowy model przy użyciu trzech typów jednostek](./media/association-set/example-model-three-entity-types.gif)  
  
 W poniższym przykładzie przedstawiono zestaw skojarzeń (`PublishedBy`) i dwa zestawy jednostek (`Books` i `Publishers`) oparte na modelu koncepcyjnego przedstawionych powyżej. Analizy biznesowej w `Books` zestaw jednostek reprezentuje wystąpienie `Book` typu jednostki w czasie wykonywania. Podobnie, reprezentuje Pj `Publisher` wystąpienia w `Publishers` zestawu jednostek. BiPj reprezentuje wystąpienie `PublishedBy` skojarzenia w `PublishedBy` zestaw skojarzeń.  
  
 ![Zrzut ekranu przedstawia przykład zestawów.](./media/association-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujące CSDL definiuje kontener jednostek z jednej skojarzenia dla każdego skojarzenia na powyższym diagramie. Należy zauważyć, że nazwa i skojarzenia dla każdego skojarzenia należy ustawić są definiowane przy użyciu atrybutów XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Można zdefiniować wiele zestawów skojarzeń na skojarzenie, tak długo, jak nie skojarzenie dwóch zestawów udziału [punkt końcowy zestawu skojarzeń](../../../../docs/framework/data/adonet/association-set-end.md). Następujące CSDL definiuje kontener jednostek z dwoma zestawami skojarzenia dla `WrittenBy` skojarzenia. Należy zauważyć, że wiele zestawów jednostki zostały zdefiniowane dla `Book` i `Author` typów jednostek oraz czy żadne skojarzenia udziałów skojarzenie punkt końcowy zestawu.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
- [właściwość klucza obcego](../../../../docs/framework/data/adonet/foreign-key-property.md)
