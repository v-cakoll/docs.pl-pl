---
title: facet
ms.date: 03/30/2017
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
ms.openlocfilehash: 0157105290a297eff2c1bf799a2065872082e40e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735641"
---
# <a name="facet"></a>facet
Zestaw *reguł* służy do dodawania szczegółów do definicji właściwości typu pierwotnego. Definicja [Właściwości](property.md) zawiera informacje o typie właściwości, ale często więcej szczegółów jest konieczna. Na przykład typ jednostki w modelu koncepcyjnym może mieć właściwość typu `String` której wartość nie może być ustawiona na wartość null. Zestawy reguł umożliwiają określenie tego poziomu szczegółowości.  
  
 W poniższej tabeli opisano aspekty, które są obsługiwane w modelu EDM.  
  
> [!NOTE]
> Dokładne wartości i zachowania aspektów są określane przez środowisko uruchomieniowe, które korzysta z implementacji modelu EDM.  
  
|Aspekcie|Opis|Informacje zawarte w tym artykule dotyczą|  
|-----------|-----------------|----------------|  
|`Collation`|Określa sekwencję sortowania (lub sekwencję sortowania), która ma być używana podczas wykonywania operacji porównania i porządkowania na wartościach właściwości.|`String`|  
|`ConcurrencyMode`|Wskazuje, że wartość właściwości powinna być używana do optymistycznych kontroli współbieżności.|Wszystkie właściwości typu pierwotnego|  
|`Default`|Określa wartość domyślną właściwości, jeśli nie podano żadnej wartości podczas tworzenia wystąpienia.|Wszystkie właściwości typu pierwotnego|  
|`FixedLength`|Określa, czy długość wartości właściwości może się różnić.|`Binary`, `String`|  
|`MaxLength`|Określa maksymalną długość wartości właściwości.|`Binary`, `String`|  
|`Nullable`|Określa, czy właściwość może mieć wartość null.|Wszystkie właściwości typu pierwotnego|  
|`Precision`|Dla właściwości typu `Decimal`określa liczbę cyfr, jaką może mieć wartość właściwości. Dla właściwości typu `Time`, `DateTime`i `DateTimeOffset`określa liczbę cyfr ułamkowej części sekundy wartości właściwości.|`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,|  
|`Scale`|Określa liczbę cyfr z prawej strony punktu dziesiętnego dla wartości właściwości.|Wartość dziesiętna|  
|`Unicode`|Wskazuje, czy wartość właściwości jest przechowywana w formacie Unicode.|`String`|  
  
## <a name="example"></a>Przykład  
 [ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych. Poniższy element CSDL definiuje `Book` typ jednostki. Należy zauważyć, że zestawy reguł są implementowane jako atrybuty XML. Wartości aspektów wskazują, że żadna właściwość nie może być ustawiona na wartość null i że `Scale` i `Precision` właściwości `Revision` są ustawione na 29.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
