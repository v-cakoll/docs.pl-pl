---
title: 'Entity Data Model: dziedziczenie'
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: 4c4abc371000006d40ede3d904b0437f3f85e3e7
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738451"
---
# <a name="entity-data-model-inheritance"></a>Entity Data Model: dziedziczenie
Entity Data Model (EDM) obsługuje dziedziczenie dla [typów jednostek](entity-type.md). Dziedziczenie w modelu EDM jest podobne do dziedziczenia klas w językach programowania zorientowanego obiektowo. Podobnie jak w przypadku klas w językach zorientowanych obiektowo, w modelu koncepcyjnym można zdefiniować typ jednostki ( *Typ pochodny*), który dziedziczy z innego typu jednostki ( *Typ podstawowy*). Jednak w przeciwieństwie do klas w programowaniu zorientowanym na obiektach, w modelu koncepcyjnym typ pochodny zawsze dziedziczy wszystkie [Właściwości](property.md) i [właściwości nawigacji](navigation-property.md) typu podstawowego. Nie można przesłonić dziedziczonych właściwości w typie pochodnym.  
  
 W modelu koncepcyjnym można tworzyć hierarchie dziedziczenia, w których typ pochodny dziedziczy z innego typu pochodnego. Typ w górnej części hierarchii (jeden typ w hierarchii, która nie jest typem pochodnym) jest nazywany *typem głównym*. W hierarchii dziedziczenia [klucz jednostki](entity-key.md) musi być zdefiniowany w typie głównym.  
  
 Nie można skompilować hierarchii dziedziczenia, w których typ pochodny dziedziczy z więcej niż jednego typu. Na przykład w modelu koncepcyjnym z typem jednostki `Book` można zdefiniować typy pochodne `FictionBook` i `NonFictionBook`, które dziedziczą z `Book`. Nie można jednak zdefiniować typu, który dziedziczy z obu typów `FictionBook` i `NonFictionBook`.  
  
## <a name="example"></a>Przykład  

Na poniższym diagramie przedstawiono model koncepcyjny z czterema typami jednostek: `Book`, `FictionBook`, `Publisher`i `Author`. Typ jednostki `FictionBook` jest typem pochodnym, który dziedziczy z typu jednostki `Book`. Typ `FictionBook` dziedziczy właściwości `ISBN (Key)`, `Title`i `Revision` i definiuje dodatkową właściwość o nazwie `Genre`.  
  
 ![Diagram przedstawiający model koncepcyjny z czterema typami jednostek.](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych. Poniższy identyfikator CSDL definiuje typ jednostki `FictionBook`, który dziedziczy z typu `Book` (jak na poniższym diagramie):  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
