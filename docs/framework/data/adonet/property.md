---
title: property
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: bc8f890479e195f1e6ef847219a74f165c722fd6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589428"
---
# <a name="property"></a>property
*Właściwości* są podstawowymi blokami konstrukcyjnymi miejsc z [typów jednostek](../../../../docs/framework/data/adonet/entity-type.md) i [typy złożone](../../../../docs/framework/data/adonet/complex-type.md). Właściwości definiują kształt i charakterystyki danych, która będzie zawierać wystąpienia typu jednostki lub typ złożony. Właściwości w modelu koncepcyjnym są analogiczne do właściwości zdefiniowane w klasie. W ten sam sposób, że właściwości w klasie określenia kształtu elementu klasy i zawierają informacje o obiektach właściwości w modelu koncepcyjnym określenia kształtu typu jednostki i zawierają informacje na temat wystąpień typu jednostki.  
  
> [!NOTE]
>  Właściwości, zgodnie z opisem w tym temacie różnią się od właściwości nawigacji. Aby uzyskać więcej informacji, zobacz [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md).  
  
 Definicja właściwości zawiera następujące informacje:  
  
-   Nazwa właściwości. (Wymagane)  
  
-   Typ właściwości. (Wymagane)  
  
-   Zbiór [aspektami](../../../../docs/framework/data/adonet/facet.md). (opcjonalnie)  
  
 Właściwość może zawierać danych pierwotnych (na przykład ciąg, liczba całkowita lub wartość logiczna) lub dane strukturalne (takie jak typ złożony). Pierwotny typ właściwości są również nazywane właściwości skalarne. Aby uzyskać więcej informacji, zobacz [modelu danych jednostki: Pierwotne typy danych](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
> [!NOTE]
>  Typ złożony sam mają właściwości, które są typy złożone.  
  
## <a name="example"></a>Przykład  
 Poniższy diagram przedstawia modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`. Każdy typ jednostki ma kilka właściwości, mimo że nie zamieszczono informacje o typie dla każdej właściwości w schemacie. Właściwości, które są [klucze jednostek](../../../../docs/framework/data/adonet/entity-key.md) są oznaczone symbolem (klucz).  
  
 ![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Definiuje następujące CSDL `Book` jednostki typu (jak pokazano na powyższym diagramie) i wskazuje typ i nazwa każdej właściwości przy użyciu atrybutów XML. Opcjonalnie zestawu reguł, `Nullable`, jest również definiowany przy użyciu atrybutu XML.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Istnieje możliwość, że jedna z właściwości wyświetlane na diagramie jest właściwość typu złożonego. Na przykład `Address` właściwość `Publisher` typu jednostki może być właściwość typu złożonego składa się z kilku właściwości skalarne, takie jak `StreetAddress`, `City`, `StateOrProvince`, `Country`, i `PostalCode`. Reprezentacja CSDL typu złożonego będzie następujący:  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a>Zobacz także
- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
