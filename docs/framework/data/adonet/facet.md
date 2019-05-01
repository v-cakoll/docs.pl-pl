---
title: facet
ms.date: 03/30/2017
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
ms.openlocfilehash: 9353b143a328e0fb183b7870332462a0a2c91b10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879063"
---
# <a name="facet"></a>facet
A *aspekt* służy do dodawania szczegółów do definicji właściwości typu pierwotnego. A [właściwość](../../../../docs/framework/data/adonet/property.md) definicja zawiera informacje o typie właściwości, ale często konieczne jest bardziej szczegółowo. Na przykład typ jednostki w modelu koncepcyjnym może mieć właściwości typu `String` wartości, których nie można ustawić na wartość null. Aspekty umożliwiają określenie tego poziomu szczegółowości.  
  
 W poniższej tabeli opisano aspekty, które są obsługiwane przez EDM.  
  
> [!NOTE]
>  Dokładne wartości i zachowania zestawów reguł są określane przez środowisko wykonawcze, korzystającą z implementacji EDM.  
  
|zestaw reguł|Opis|Informacje zawarte w tym artykule dotyczą|  
|-----------|-----------------|----------------|  
|`Collation`|Określa kolejność sortowania (lub sekwencji sortowania) do użycia podczas przeprowadzania porównania i kolejność operacji na wartościach właściwości.|`String`|  
|`ConcurrencyMode`|Wskazuje, że wartość właściwości powinien być używany w celu pomyślnych kontroli współbieżności.|Wszystkie właściwości typu pierwotnego|  
|`Default`|Określa domyślną wartość właściwości, jeśli nie dostarczono żadnej wartości dla wystąpienia.|Wszystkie właściwości typu pierwotnego|  
|`FixedLength`|Określa, czy długość wartości właściwości mogą się różnić.|`Binary`, `String`|  
|`MaxLength`|Określa maksymalną długość wartości właściwości.|`Binary`, `String`|  
|`Nullable`|Określa, czy właściwość może mieć wartości null.|Wszystkie właściwości typu pierwotnego|  
|`Precision`|Dla właściwości typu `Decimal`, określa liczbę cyfr, może mieć wartości właściwości. Dla właściwości typu `Time`, `DateTime`, i `DateTimeOffset`, określa liczbę cyfr ułamkowych części sekundy w wartości właściwości.|`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,|  
|`Scale`|Określa liczbę cyfr po prawej stronie przecinka dziesiętnego dla wartości właściwości.|Wartość dziesiętna|  
|`Unicode`|Wskazuje, czy wartość właściwości jest przechowywana jako Unicode.|`String`|  
  
## <a name="example"></a>Przykład  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Definiuje następujące CSDL `Book` typu jednostki. Należy pamiętać, że zestawy reguł są implementowane jako atrybuty XML. Wartości aspektu wskazują, że nie ma właściwości można ustawić wartość null, a `Scale` i `Precision` z `Revision` są każdego ustawioną 29.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
