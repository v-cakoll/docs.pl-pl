---
title: 'Model danych jednostki: Dziedziczenie'
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: 21dbdff63c07dbcdac8de7bf4b3a8e5d0ece7901
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784067"
---
# <a name="entity-data-model-inheritance"></a>Model danych jednostki: Dziedziczenie
Entity Data Model (EDM) obsługuje dziedziczenie dla [typów jednostek](entity-type.md). Dziedziczenie w modelu EDM jest podobne do dziedziczenia klas w językach programowania zorientowanego obiektowo. Podobnie jak w przypadku klas w językach zorientowanych obiektowo, w modelu koncepcyjnym można zdefiniować typ jednostki ( *Typ pochodny*), który dziedziczy z innego typu jednostki ( *Typ podstawowy*). Jednak w przeciwieństwie do klas w programowaniu zorientowanym na obiektach, w modelu koncepcyjnym typ pochodny zawsze dziedziczy wszystkie [Właściwości](property.md) i [właściwości nawigacji](navigation-property.md) typu podstawowego. Nie można przesłonić dziedziczonych właściwości w typie pochodnym.  
  
 W modelu koncepcyjnym można tworzyć hierarchie dziedziczenia, w których typ pochodny dziedziczy z innego typu pochodnego. Typ w górnej części hierarchii (jeden typ w hierarchii, która nie jest typem pochodnym) jest nazywany *typem głównym*. W hierarchii dziedziczenia [klucz jednostki](entity-key.md) musi być zdefiniowany w typie głównym.  
  
 Nie można skompilować hierarchii dziedziczenia, w których typ pochodny dziedziczy z więcej niż jednego typu. Na przykład w modelu `Book` koncepcyjnym z typem jednostki można zdefiniować typy `FictionBook` pochodne i `NonFictionBook` każdy z `Book`nich dziedziczy. Nie można jednak zdefiniować typu, który dziedziczy z obu `FictionBook` typów i. `NonFictionBook`  
  
## <a name="example"></a>Przykład  

Na poniższym diagramie przedstawiono model koncepcyjny z czterema typami jednostek: `Book`, `FictionBook`, `Publisher`, i `Author`. Typ jednostki jest typem pochodnym, który dziedziczy `Book` z typu jednostki. `FictionBook` `FictionBook` Typ `Genre`dziedziczy właściwości `Title`,, i`Revision` i definiuje dodatkową właściwość o nazwie. `ISBN (Key)`  
  
 ![Diagram przedstawiający model koncepcyjny z czterema typami jednostek.](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Poniższy identyfikator CSDL definiuje typ `FictionBook`jednostki, który dziedziczy `Book` z typu (jak na diagramie powyżej):  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
