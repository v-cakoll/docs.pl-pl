---
title: Zestaw jednostek
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 5a8b4bdac2d0cb2065438bb390c002fcb690b1f6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764141"
---
# <a name="entity-set"></a>Zestaw jednostek
*Zestaw jednostek* jest kontenerem logicznym dla wystąpień [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) i wystąpień dowolnego typu pochodzącego od tego typu jednostki. (Informacje o typach pochodnych, zobacz [modelu Entity Data Model: dziedziczenie](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) Relacja między typem obiektu a zestaw jednostek jest odpowiednikiem relację wiersz tabeli relacyjnej bazy danych: jak wiersz, typem jednostki opisuje struktura danych i, jak tabelę, zestaw jednostek zawiera wystąpień danego struktury. Zestaw jednostek nie jest danych modelowania konstrukcji; nie opisano w strukturze danych. Zamiast tego zestawu jednostek zapewnia konstrukcję w środowisku obsługującym lub magazynu (na przykład środowisko uruchomieniowe języka wspólnego lub bazy danych programu SQL Server) do wystąpień typów jednostek grupy mogą być mapowane do magazynu danych.  
  
 Zestaw jednostek jest zdefiniowany w [kontenera jednostek](../../../../docs/framework/data/adonet/entity-container.md), która jest logiczne grupowanie zestawów jednostek i [ustawia skojarzenie](../../../../docs/framework/data/adonet/association-set.md).  
  
 W przypadku wystąpienia typu jednostki istnieje w zestawie jednostek musi spełnienia następujących warunków:  
  
-   Typ wystąpienia jest ona taka sama jak typ jednostki, na którym jest oparty ten zestaw jednostek lub typ wystąpienia jest podtypem typu jednostki.  
  
-   [Klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) wystąpienie jest unikatowa w obrębie zestawu jednostek.  
  
-   Wystąpienie nie istnieje w innym zestawie jednostek.  
  
    > [!NOTE]
    >  Wiele zestawów jednostek można zdefiniować przy użyciu tego samego typu jednostki, ale wystąpienie typu danej jednostki może istnieć tylko w zestawie jedną jednostkę.  
  
 Nie trzeba zdefiniować zestaw jednostek dla poszczególnych typów jednostek w modelu koncepcyjnym.  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`.  
  
 ![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Na poniższym diagramie przedstawiono dwa zestawy jednostek (`Books` i `Publishers`) i zestaw skojarzeń (`PublishedBy`) oparte na modelu koncepcyjnego przedstawionych powyżej. Analizy biznesowej w `Books` zestaw jednostek reprezentuje wystąpienie `Book` typu jednostki w czasie wykonywania. Podobnie, uzyskać reprezentują `Publisher` wystąpienia w `Publishers` zestawu jednostek. BiPj reprezentuje wystąpienie `PublishedBy` skojarzenia w `PublishedBy` zestawu skojarzeń.  
  
 ![Ustawia przykład](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujący plik CSDL definiuje kontenera jednostek o jeden zestaw jednostek dla poszczególnych typów jednostek w modelu koncepcyjnym przedstawionych powyżej. Należy pamiętać, że typ nazwy i jednostki dla każdego zestawu jednostek są zdefiniowane przy użyciu atrybutów XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Istnieje możliwość definiowania wielu zestawów jednostek na typ (MEST). Następujący plik CSDL definiuje kontenera jednostek z dwóch zestawów jednostek dla `Book` typ jednostki:  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
