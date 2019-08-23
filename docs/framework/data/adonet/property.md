---
title: property
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: 59b4ccf18b0e1f9054fd2a253fcd39072ed10e98
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946283"
---
# <a name="property"></a>property
*Właściwości* są podstawowymi blokami konstrukcyjnymi [typów jednostek](../../../../docs/framework/data/adonet/entity-type.md) i [typów złożonych](../../../../docs/framework/data/adonet/complex-type.md). Właściwości definiują kształt i charakterystykę danych, które będzie zawierać wystąpienie typu jednostki lub wystąpienie typu złożonego. Właściwości w modelu koncepcyjnym są analogiczne do właściwości zdefiniowanych w klasie. W taki sam sposób, w jaki właściwości klasy definiują kształt klasy i zawierają informacje o obiektach, właściwości w modelu koncepcyjnym definiują kształt typu jednostki i zawierają informacje o wystąpieniach typu jednostki.  
  
> [!NOTE]
> Właściwości, zgodnie z opisem w tym temacie, różnią się od właściwości nawigacji. Aby uzyskać więcej informacji, zobacz [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md).  
  
 Definicja właściwości zawiera następujące informacje:  
  
- Nazwa właściwości. Potrzeb  
  
- Typ właściwości. Potrzeb  
  
- Zestaw aspektów [](../../../../docs/framework/data/adonet/facet.md). (opcjonalnie)  
  
 Właściwość może zawierać dane pierwotne (takie jak ciąg, liczba całkowita lub wartość logiczna) lub dane strukturalne (takie jak typ złożony). Właściwości typu pierwotnego są również nazywane właściwościami skalarnymi. Aby uzyskać więcej informacji, [zobacz Entity Data Model: Typy](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)danych pierwotnych.  
  
> [!NOTE]
> Typ złożony może sam, mieć właściwości, które są typu złożonego.  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`. Każdy typ jednostki ma kilka właściwości, chociaż informacje o typie dla każdej właściwości nie są przekazywane na diagramie. Właściwości, które są [kluczami jednostek](../../../../docs/framework/data/adonet/entity-key.md) , są oznaczane symbolem (Key).  
  
 ![Przykładowy model z trzema typami jednostek](./media/property/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Poniższy plik CSDL definiuje `Book` typ jednostki (jak pokazano na powyższym diagramie) i wskazuje typ i nazwę każdej właściwości przy użyciu atrybutów XML. Opcjonalny zestaw reguł `Nullable`,,, jest również definiowany przy użyciu atrybutu XML.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Istnieje możliwość, że jedna z właściwości pokazywanych na diagramie jest właściwością typu złożonego. Na przykład `Address` Właściwość `Country` `PostalCode` `StreetAddress` `StateOrProvince` `City`typu jednostki może być właściwością typu złożonego składającą się z kilku właściwości skalarnych, takich jak,,, i. `Publisher` Reprezentacja CSDL tego typu złożonego będzie następująca:  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
