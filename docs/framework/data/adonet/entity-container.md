---
title: kontener jednostek
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 58642c6cc794f931387ac7a76dd64d368957f14b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586963"
---
# <a name="entity-container"></a>kontener jednostek
*Kontener jednostek* jest logicznym grupowaniem [zestawy jednostek](../../../../docs/framework/data/adonet/entity-set.md), [zestawów skojarzeń](../../../../docs/framework/data/adonet/association-set.md), i [funkcji Importy](../../../../docs/framework/data/adonet/model-declared-function.md).  
  
 Wymaga spełnienia następujących warunków zdefiniowanych w modelu koncepcyjnym kontenera jednostki:  
  
- Co najmniej jedną jednostkę kontenera muszą być zdefiniowane w każdego modelu koncepcyjnego.  
  
- Kontener jednostek musi mieć unikatową nazwę w ramach każdego modelu koncepcyjnego.  
  
 Kontener jednostek można zdefiniować zestawy jednostek lub zestawów skojarzeń, które używają typów jednostek lub skojarzenia zdefiniowane w jeden lub kilka przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [modelu danych jednostki: Przestrzenie nazw](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).  
  
## <a name="example"></a>Przykład  
 Poniższy diagram przedstawia modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`.  Zobacz przykład dalej, aby uzyskać więcej informacji.  
  
 ![Przykładowy model przy użyciu trzech typów jednostek](./media/entity-container/example-model-three-entity-types.gif)  
  
 Mimo że diagram nie obejmują informacji dotyczących kontenera jednostki, model koncepcyjny zdefiniuj kontener jednostek. [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa o nazwie język definicji schematu koncepcyjnego języka DSL ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujące CSDL definiuje kontener jednostek dla modelu koncepcyjnego pokazano na powyższym diagramie. Należy pamiętać, że nazwa kontenera jednostki jest zdefiniowany w atrybut XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
