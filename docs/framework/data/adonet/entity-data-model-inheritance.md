---
title: 'Modelu danych jednostki: dziedziczenie'
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: c5c1b385ea72e48fd70ed5ec0cf8d1c42c1284e4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="entity-data-model-inheritance"></a>Modelu danych jednostki: dziedziczenie
Modelu danych jednostki (EDM) obsługuje dziedziczenia dla [typów jednostek](../../../../docs/framework/data/adonet/entity-type.md). Dziedziczenie w modelu EDM jest podobny do dziedziczenia klas w zorientowane obiektowo języków programowania. Tak jak w przypadku klas w językach zorientowane obiektowo w modelu koncepcyjnym można zdefiniować typu jednostki ( *typu pochodnego*) dziedziczący z innego typu jednostki ( *typ podstawowy*). Jednak w przeciwieństwie do klas w programowanie zorientowane obiektowo, w modelu koncepcyjnym Typ pochodny zawsze dziedziczy wszystkie [właściwości](../../../../docs/framework/data/adonet/property.md) i [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) typu podstawowego. Nie można przesłonić dziedziczonego właściwości w typie pochodnym.  
  
 W modelu koncepcyjnym można utworzyć hierarchii dziedziczenia, w których typem pochodnym dziedziczy z typu pochodnego. Typ w hierarchii (jeden typ w hierarchii, która nie jest typem pochodnym) jest nazywany *Typ główny*. W hierarchii dziedziczenia [klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) musi być zdefiniowana dla typu głównego.  
  
 Nie można utworzyć hierarchii dziedziczenia, w których typem pochodnym dziedziczy z więcej niż jednego typu. Na przykład w modelu koncepcyjnym z `Book` typu jednostki, można zdefiniować typy pochodne `FictionBook` i `NonFictionBook` czy każdy dziedziczyć `Book`. Jednak nie następnie można zdefiniować typu, który dziedziczy z obu `FictionBook` i `NonFictionBook` typów.  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z czterema typami jednostek: `Book`, `FictionBook`, `Publisher`, i `Author`. `FictionBook` Typ jednostki jest typem pochodnym dziedziczących `Book` typu jednostki. `FictionBook` Typ dziedziczy `ISBN (Key)`, `Title`, i `Revision` właściwości oraz definiuje dodatkowe właściwości o nazwie `Genre`.  
  
 ![Dziedziczenie](../../../../docs/framework/data/adonet/media/inheritanceexample.gif "InheritanceExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujące CSDL definiuje typ jednostki `FictionBook`, która dziedziczy `Book` typu (tak jak na powyższym diagramie):  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
