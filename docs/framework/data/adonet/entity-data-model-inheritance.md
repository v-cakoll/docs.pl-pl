---
title: 'Model danych jednostki: Dziedziczenie'
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: bc0467ea1b242c13e00e115f07ccbc5c840df936
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837135"
---
# <a name="entity-data-model-inheritance"></a>Model danych jednostki: Dziedziczenie
Entity Data Model (EDM) obsługuje dziedziczenie [typów jednostek](../../../../docs/framework/data/adonet/entity-type.md). Dziedziczenie w EDM jest podobny do dziedziczenia klas w językach programowania obiektowego. Tak jak w przypadku klas w językach obiektowych w modelu koncepcyjnym można zdefiniować typ jednostki ( *typu pochodnego*) który dziedziczy z innego typu jednostki ( *typ podstawowy*). Jednak w odróżnieniu od klas w programowanie zorientowane obiektowo, w modelu koncepcyjnym Typ pochodny zawsze dziedziczy wszystkie [właściwości](../../../../docs/framework/data/adonet/property.md) i [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) typu podstawowego. Nie można zastąpić właściwości dziedziczonych w typie pochodnym.  
  
 W modelu koncepcyjnym można tworzyć hierarchie dziedziczenia, w których typ pochodny dziedziczy z innego typu pochodnego. Typ w hierarchii (jeden typ w hierarchii, który nie jest typem pochodnym) jest nazywany *główny typ*. W hierarchii dziedziczenia [klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) muszą być zdefiniowane w typie katalogu głównego.  
  
 Nie można utworzyć hierarchii dziedziczenia, w których typ pochodny dziedziczy z więcej niż jednego typu. Na przykład w modelu koncepcyjnego z `Book` typu jednostki, można zdefiniować typy pochodne `FictionBook` i `NonFictionBook` , każdy dziedziczyć `Book`. Jednak nie następnie można zdefiniować typ, który dziedziczy z obu `FictionBook` i `NonFictionBook` typów.  
  
## <a name="example"></a>Przykład  

Na poniższym diagramie przedstawiono model koncepcyjny przy użyciu czterech typów jednostek: `Book`, `FictionBook`, `Publisher`, i `Author`. `FictionBook` Typ jednostki jest typ pochodny dziedziczy z `Book` typu jednostki. `FictionBook` Typ dziedziczy `ISBN (Key)`, `Title`, i `Revision` właściwości i definiuje dodatkowe właściwości o nazwie `Genre`.  
  
 ![Diagram pokazujący model koncepcyjny przy użyciu czterech typów jednostek.](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujące CSDL definiuje typ jednostki, `FictionBook`, która dziedziczy z `Book` typu (tak jak w powyższym diagramie):  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Zobacz także
- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
