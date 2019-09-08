---
title: klucz jednostki
ms.date: 03/30/2017
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
ms.openlocfilehash: db867b3a853bd29f1faf1be2faf77776e48be2d2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795140"
---
# <a name="entity-key"></a>klucz jednostki
*Klucz jednostki* jest [właściwością](property.md) lub zestawem właściwości [typu jednostki](entity-type.md) , które są używane do określania tożsamości. Właściwości tworzące klucz jednostki są wybierane w czasie projektowania. Wartości właściwości klucza jednostki muszą jednoznacznie identyfikować wystąpienie typu jednostki w ramach [zestawu jednostek](entity-set.md) w czasie wykonywania. Właściwości tworzące klucz jednostki powinny być wybierane w celu zagwarantowania unikatowej wartości wystąpień w zestawie jednostek.  
  
 Poniżej przedstawiono wymagania dotyczące zestawu właściwości jako klucza jednostki:  
  
- Nie mogą być identyczne dwa klucze jednostek w ramach zestawu jednostek. Oznacza to, że dla wszystkich dwóch jednostek w ramach zestawu jednostek wartości dla wszystkich właściwości, które stanowią klucz, nie mogą być takie same. Jednak niektóre (ale nie wszystkie) wartości, które składają się na klucz jednostki, mogą być takie same.  
  
- Klucz jednostki musi składać się z zestawu właściwości niedopuszczających wartości null, niezmiennego [typu podstawowego](entity-data-model-primitive-data-types.md).  
  
- Nie można zmienić właściwości, które składają się na klucz jednostki dla danego typu jednostki. Nie można zezwolić na więcej niż jeden możliwy klucz jednostki dla danego typu jednostki; klucze zastępcze nie są obsługiwane.  
  
- Gdy jednostka jest uwzględniona w hierarchii dziedziczenia, jednostka główna musi zawierać wszystkie właściwości tworzące klucz jednostki, a klucz jednostki musi być zdefiniowany w typie jednostki głównej. Aby uzyskać więcej informacji, [zobacz Entity Data Model: Dziedziczenie](entity-data-model-inheritance.md).  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`. Właściwości każdego typu jednostki, który tworzą swój klucz jednostki, są oznaczane "(kluczem)". Należy zauważyć, `Author` że typ jednostki ma klucz jednostki składający się z dwóch właściwości `Name` , `Address`i.  
  
 ![Przykładowy model z trzema typami jednostek](./media/entity-key/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. W obszarze CSDL poniżej zdefiniowano `Book` typ jednostki przedstawiony na powyższym diagramie. Należy pamiętać, że klucz jednostki jest definiowany przez odwołanie `ISBN` się do właściwości typu jednostki.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 `ISBN` Właściwość jest dobrym wyborem dla klucza jednostki, ponieważ międzynarodowy numer książki standardowej (ISBN) jednoznacznie identyfikuje książkę.  
  
 W obszarze CSDL poniżej zdefiniowano `Author` typ jednostki przedstawiony na powyższym diagramie. Należy zauważyć, że klucz jednostki składa się z `Name` dwóch `Address`właściwości, i.  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 Korzystanie `Name` z `Address` i dla klucza jednostki jest rozsądnie możliwe, ponieważ dwa autorów o tej samej nazwie jest mało prawdopodobne, aby na tym samym adresie były wyświetlane. Jednak wybór dla klucza jednostki nie gwarantuje jednowzględnie unikatowych kluczy jednostki w zestawie jednostek. W takim przypadku zaleca się dodanie `AuthorId`właściwości, takiej jak, która może zostać użyta do unikatowej identyfikacji autora.  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
