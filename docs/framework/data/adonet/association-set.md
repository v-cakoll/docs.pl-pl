---
title: "zestawu skojarzeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: db293cbc636d0ae4e532f24b2852444395f603c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="association-set"></a>zestawu skojarzeń
*Zestawu skojarzeń* jest kontenerem logicznym dla [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) wystąpień tego samego typu. Zestaw skojarzenia nie jest danych modelowania konstrukcji; oznacza to, że nie opisano struktury danych lub relacji. Zamiast tego zestawu skojarzeń zapewnia konstrukcję w środowisku obsługującym lub magazynu (na przykład środowisko uruchomieniowe języka wspólnego lub bazy danych programu SQL Server) do wystąpień skojarzenie grupy mogą być mapowane do magazynu danych.  
  
 Zestaw skojarzenia są zdefiniowane w obrębie [kontenera jednostek](../../../../docs/framework/data/adonet/entity-container.md), która jest logiczną grupę [zestawów jednostek](../../../../docs/framework/data/adonet/entity-set.md) i zestawy skojarzeń.  
  
 Definicja zestawu skojarzeń zawiera następujące informacje:  
  
-   Nazwa zestawu skojarzeń. (Wymagane)  
  
-   Skojarzenia, z których będzie zawierać wystąpień. (Wymagane)  
  
-   Dwa [skojarzenia ustawić kończy się](../../../../docs/framework/data/adonet/association-set-end.md).  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z dwóch skojarzenia: `PublishedBy`, i `WrittenBy`. Chociaż informacje o zestawach skojarzenia nie jest przekazywany w schemacie, diagram dalej przedstawiono przykład skojarzenia zestawów i zestawów jednostek na podstawie tego modelu.  
  
 ![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 W poniższym przykładzie przedstawiono zestawu skojarzeń (`PublishedBy`) i dwa zestawy jednostek (`Books` i `Publishers`) oparte na modelu koncepcyjnego przedstawionych powyżej. Analizy biznesowej w `Books` zestaw jednostek reprezentuje wystąpienie `Book` typu jednostki w czasie wykonywania. Podobnie, uzyskać reprezentuje `Publisher` wystąpienia w `Publishers` zestawu jednostek. BiPj reprezentuje wystąpienie `PublishedBy` skojarzenia w `PublishedBy` zestawu skojarzeń.  
  
 ![Ustawia przykład](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujący plik CSDL definiuje kontenera jednostek z jednego zestawu dla każdego skojarzenia na powyższym diagramie skojarzeń. Należy pamiętać, że nazwa i skojarzenia dla każdego skojarzenia są zdefiniowane przy użyciu atrybutów XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Można zdefiniować wiele zestawów skojarzenie na skojarzenie tak długo, jak nie skojarzenie dwóch zestawów udziału [Konfigurowanie skojarzenia](../../../../docs/framework/data/adonet/association-set-end.md). Następujący plik CSDL definiuje kontenera jednostek z dwoma zestawami skojarzenia dla `WrittenBy` skojarzenia. Należy zauważyć, że wiele zestawów jednostek zostały zdefiniowane dla `Book` i `Author` Konfigurowanie typów jednostek i że żaden związek ustawić udziały skojarzenia.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [Właściwość klucza obcego](../../../../docs/framework/data/adonet/foreign-key-property.md)
