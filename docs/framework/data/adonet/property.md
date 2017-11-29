---
title: property
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c052c53488fde0ea767a46f51ef349dd6a7d2766
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="property"></a>property
*Właściwości* są podstawowymi blokami konstrukcyjnymi elementu [typów jednostek](../../../../docs/framework/data/adonet/entity-type.md) i [typów złożonych](../../../../docs/framework/data/adonet/complex-type.md). Właściwości definiują kształt i właściwości danych, który będzie zawierać wystąpienia typu jednostki lub typu złożonego. Właściwości w modelu koncepcyjnym są analogiczne do właściwości zdefiniowane w klasie. W ten sam sposób, że właściwości dla klasy, zdefiniuj kształtu klasy i zawiera informacje o obiektach właściwości w modelu koncepcyjnym zdefiniuj kształtu typu jednostki i zawiera informacje na temat wystąpień typu jednostki.  
  
> [!NOTE]
>  Właściwości, zgodnie z opisem w tym temacie różnią się od właściwości nawigacji. Aby uzyskać więcej informacji, zobacz [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md).  
  
 Definicja właściwości zawiera następujące informacje:  
  
-   Nazwa właściwości. (Wymagane)  
  
-   Typ właściwości. (Wymagane)  
  
-   Zestaw [aspekty](../../../../docs/framework/data/adonet/facet.md). (opcjonalnie)  
  
 Właściwość może zawierać danych pierwotnych (na przykład ciągiem, liczbą całkowitą lub wartość logiczną) lub dane strukturalne (takie jak typ złożony). Właściwości typu pierwotnego są również nazywane właściwości skalarne. Aby uzyskać więcej informacji, zobacz [modelu Entity Data Model: typy pierwotne danych](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
> [!NOTE]
>  Typ złożony mają właściwości, które są typami złożonymi.  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`. Poszczególnych typów jednostek ma kilka właściwości, chociaż nie przekazywanych informacji o typie dla każdej właściwości w schemacie. Właściwości, które są [kluczy jednostek](../../../../docs/framework/data/adonet/entity-key.md) są oznaczone symbolem (Key).  
  
 ![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Definiuje następujące CSDL `Book` jednostki typu (jak pokazano na powyższym diagramie) oraz wskazuje typ i nazwa każdej właściwości przy użyciu atrybutów XML. Opcjonalne aspektu `Nullable`, jest także zdefiniowana przy użyciu atrybutu XML.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Istnieje możliwość, że jedna z właściwości wyświetlane na diagramie jest właściwość typu złożonego. Na przykład `Address` właściwość `Publisher` typu jednostki można właściwość typu złożonego złożony z kilku właściwości skalarne, takie jak `StreetAddress`, `City`, `StateOrProvince`, `Country`, i `PostalCode`. Reprezentacja CSDL typu złożonego, należy w następujący sposób:  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
