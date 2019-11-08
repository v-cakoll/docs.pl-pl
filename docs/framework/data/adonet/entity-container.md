---
title: kontener jednostek
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 0c194d86e6276c948a545f830e569cbc68f86a14
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737870"
---
# <a name="entity-container"></a>kontener jednostek
*Kontener jednostek* jest logiczną grupą [zestawów jednostek](entity-set.md), [zestawów skojarzeń](association-set.md)i [importów funkcji](model-declared-function.md).  
  
 Następujące elementy muszą mieć wartość true kontenera Entity zdefiniowanego w modelu koncepcyjnym:  
  
- W każdym modelu koncepcyjnym musi być zdefiniowany co najmniej jeden kontener jednostek.  
  
- Kontener jednostek musi mieć unikatową nazwę w ramach każdego modelu koncepcyjnego.  
  
 Kontener jednostek może definiować zestawy jednostek lub zestawy skojarzeń, które używają typów jednostek lub skojarzeń zdefiniowanych w co najmniej jednym obszarze nazw. Aby uzyskać więcej informacji, zobacz [Entity Data Model: przestrzenie nazw](entity-data-model-namespaces.md).  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`.  Aby uzyskać więcej informacji, zobacz następny przykład.  
  
 ![Przykładowy model z trzema typami jednostek](./media/entity-container/example-model-three-entity-types.gif)  
  
 Chociaż diagram nie przekazuje informacji kontenera jednostki, model koncepcyjny musi definiować kontener jednostek. [ADO.NET Entity Framework](./ef/index.md) używa języka DSL o nazwie koncepcyjny schemat definicji schematu ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych. Następujący CSDL definiuje kontener jednostek dla modelu koncepcyjnego przedstawiony na powyższym diagramie. Należy zauważyć, że nazwa kontenera jednostek jest zdefiniowana w atrybucie XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
