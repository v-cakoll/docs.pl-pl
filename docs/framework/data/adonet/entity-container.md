---
title: Kontenera jednostek
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5ac4383e68aad49af1a65988d9993f6fa018b31a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="entity-container"></a>Kontenera jednostek
*Kontenera jednostek* to logiczne grupowanie [zestawów jednostek](../../../../docs/framework/data/adonet/entity-set.md), [ustawia skojarzenie](../../../../docs/framework/data/adonet/association-set.md), i [importów funkcji](../../../../docs/framework/data/adonet/model-declared-function.md).  
  
 Wymaga spełnienia następujących warunków kontenera jednostek zdefiniowanych w modelu koncepcyjnym:  
  
-   Co najmniej jedną jednostkę kontenera musi być zdefiniowana w każdym modelu koncepcyjnego.  
  
-   Kontenera jednostek musi mieć unikatową nazwę w ramach każdego modelu koncepcyjnego.  
  
 Kontenera jednostek można zdefiniować zestawy jednostek lub zestawy skojarzenia, używające typy jednostek i skojarzenia zdefiniowane w jedną lub kilka przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [modelu Entity Data Model: przestrzenie nazw](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`.  Zapoznaj się z przykładem dalej, aby uzyskać więcej informacji.  
  
 ![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Mimo że diagram nie mogą służyć do przekazywania informacji kontenera jednostek, modelu koncepcyjnego musi definiować kontenera jednostek. [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa DSL, nazywany języka definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujący plik CSDL definiuje kontenera jednostek dla modelu koncepcyjnego pokazano na powyższym diagramie. Należy pamiętać, że nazwa kontenera jednostek jest zdefiniowany w atrybutu XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
