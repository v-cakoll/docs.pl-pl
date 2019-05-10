---
title: zestaw jednostek
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: da70d25790918340e92df83b1c2c704c5dc54226
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599634"
---
# <a name="entity-set"></a>zestaw jednostek
*Zestaw jednostek* to kontener logiczny dla wystąpień [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) i wystąpień dowolnego typu opracowane z tego typu jednostki. (Aby uzyskać informacji na temat typów pochodnych, zobacz [modelu danych jednostki: Dziedziczenie](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) Relacja między typem encji i zestaw jednostek jest analogiczna do relację wiersz tabeli w relacyjnej bazie danych: Np. wiersz typ jednostki opisujący strukturę danych i jak tabela, zestaw jednostek zawiera wystąpień danego struktury. Zestaw jednostek nie jest konstrukcja; modelowania danych nie opisano w strukturze danych. Zamiast tego zestaw jednostek zapewnia konstrukcję w środowisku hostingu lub magazynu (np. środowisko uruchomieniowe języka wspólnego lub bazą danych programu SQL Server) do wystąpienia typu jednostki grupy, dzięki czemu mogą być mapowane do magazynu danych.  
  
 Zestaw jednostek jest zdefiniowana w [kontener jednostek](../../../../docs/framework/data/adonet/entity-container.md), który jest logicznym grupowaniem zestawów encji i [zestawów skojarzeń](../../../../docs/framework/data/adonet/association-set.md).  
  
 Dla wystąpienia typu jednostki, która istnieje w zestawie jednostek, wymaga spełnienia następujących warunków:  
  
- Typ wystąpienia jest taki sam jak typ jednostki, na którym jest oparty ten zestaw jednostki lub typ wystąpienia jest podtypem typu jednostki.  
  
- [Klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) wystąpienie jest unikatowa w obrębie zestawu jednostek.  
  
- Wystąpienie nie istnieje w innym zestawie jednostek.  
  
    > [!NOTE]
    >  Wiele zestawów jednostek można zdefiniować przy użyciu tego samego typu jednostki, ale wystąpienie typu danej jednostki może istnieć tylko w jednej jednostce zestawie.  
  
 Nie trzeba zdefiniować zestaw jednostek dla każdego typu jednostki w modelu koncepcyjnym.  
  
## <a name="example"></a>Przykład  
 Poniższy diagram przedstawia modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`.  
  
 ![Przykładowy model przy użyciu trzech typów jednostek](./media/entity-set/example-model-three-entity-types.gif)  
  
 Na poniższym diagramie przedstawiono dwa zestawy jednostek (`Books` i `Publishers`) i powiązanie zestawu (`PublishedBy`) oparte na modelu koncepcyjnego przedstawionych powyżej. Analizy biznesowej w `Books` zestaw jednostek reprezentuje wystąpienie `Book` typu jednostki w czasie wykonywania. Podobnie, reprezentują Pj `Publisher` wystąpienia w `Publishers` zestawu jednostek. BiPj reprezentuje wystąpienie `PublishedBy` skojarzenia w `PublishedBy` zestaw skojarzeń.  
  
 ![Zrzut ekranu przedstawia przykład zestawów.](./media/entity-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujące CSDL definiuje kontener jednostek o jeden zestaw jednostek dla każdego typu jednostki w modelu koncepcyjnym przedstawionych powyżej. Należy pamiętać, że typ nazwy i jednostki, dla każdego zestawu jednostek są definiowane przy użyciu atrybutów XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Istnieje możliwość definiowania wielu zestawów jednostek według typu (MEST). Następujące CSDL definiuje kontener jednostek z dwoma zestawami jednostki dla `Book` typ jednostki:  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
