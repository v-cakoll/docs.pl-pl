---
title: zestaw jednostek
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 5a2465801c270813dd7bca2144d05fa202571153
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738422"
---
# <a name="entity-set"></a>zestaw jednostek
*Zestaw jednostek* to logiczny kontener dla wystąpień [typu jednostki](entity-type.md) i wystąpień dowolnego typu pochodzącego od tego typu jednostki. (Aby uzyskać informacje o typach pochodnych, zobacz [Entity Data Model: dziedziczenie](entity-data-model-inheritance.md)). Relacja między typem jednostki a zestawem jednostek jest analogiczna do relacji między wierszem a tabelą w relacyjnej bazie danych: podobnie jak w przypadku wiersza, typ jednostki opisuje strukturę danych i, podobnie jak tabela, zestaw jednostek zawiera wystąpienia danej struktury. Zestaw jednostek nie jest konstrukcją modelowania danych; nie opisuje struktury danych. Zamiast tego zestaw jednostek zapewnia konstrukcję dla środowiska hostingu lub magazynu (na przykład środowisko uruchomieniowe języka wspólnego lub SQL Server Database) do grupowania wystąpień typu jednostki, dzięki czemu można je mapować do magazynu danych.  
  
 Zestaw jednostek jest zdefiniowany w [kontenerze jednostek](entity-container.md), który jest logicznym grupowaniem zestawów jednostek i [zestawów skojarzeń](association-set.md).  
  
 W przypadku wystąpienia typu jednostki, które ma istnieć w zestawie jednostek, muszą być spełnione następujące warunki:  
  
- Typ wystąpienia jest taki sam jak typ jednostki, na której bazuje zestaw jednostek lub typ wystąpienia jest podtypem typu jednostki.  
  
- [Klucz jednostki](entity-key.md) dla wystąpienia jest unikatowy w ramach zestawu jednostek.  
  
- Wystąpienie nie istnieje w żadnym innym zestawie jednostek.  
  
    > [!NOTE]
    > Wiele zestawów jednostek można zdefiniować przy użyciu tego samego typu jednostki, ale wystąpienie danego typu jednostki może istnieć tylko w jednym zestawie jednostek.  
  
 Nie trzeba definiować zestawu jednostek dla każdego typu jednostki w modelu koncepcyjnym.  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`.  
  
 ![Przykładowy model z trzema typami jednostek](./media/entity-set/example-model-three-entity-types.gif)  
  
 Na poniższym diagramie przedstawiono dwa zestawy jednostek (`Books` i `Publishers`) oraz zestaw skojarzeń (`PublishedBy`) na podstawie modelu koncepcyjnego pokazanego powyżej. Usługa BI w zestawie jednostek `Books` reprezentuje wystąpienie typu jednostki `Book` w czasie wykonywania. Podobnie PJ reprezentuje wystąpienie `Publisher` w zestawie jednostek `Publishers`. BiPj reprezentuje wystąpienie skojarzenia `PublishedBy` w zestawie skojarzeń `PublishedBy`.  
  
 ![Zrzut ekranu pokazujący przykład zestawu.](./media/entity-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych. Poniższy identyfikator CSDL definiuje kontener jednostek z jednym zestawem jednostek dla każdego typu jednostki w modelu koncepcyjnym pokazanym powyżej. Należy zauważyć, że nazwa i typ jednostki dla każdego zestawu jednostek są zdefiniowane przy użyciu atrybutów XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Istnieje możliwość zdefiniowania wielu zestawów jednostek na typ (MEST). Następujący CSDL definiuje kontener jednostek z dwoma zestawami jednostek dla `Book` typ jednostki:  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
