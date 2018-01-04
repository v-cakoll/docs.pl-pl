---
title: facet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3dde7c08fcbdd6c69ecfd987244cb71465ce807f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="facet"></a>facet
A *aspektu* służy do dodawania szczegółów do definicji właściwości typu pierwotnego. A [właściwości](../../../../docs/framework/data/adonet/property.md) definicja zawiera informacje o typie właściwości, ale często konieczne jest bardziej szczegółowo. Na przykład typ jednostki w modelu koncepcyjnym może mieć właściwość typu `String` wartości, których nie można ustawić na wartość null. Aspekty umożliwiają określenie ten poziom szczegółowości.  
  
 W poniższej tabeli opisano aspekty, które są obsługiwane w EDM.  
  
> [!NOTE]
>  Dokładne wartości i zachowania aspekty są określane przez środowisko wykonawcze, z którego korzysta implementację EDM.  
  
|Aspekt|Opis|Informacje zawarte w tym artykule dotyczą|  
|-----------|-----------------|----------------|  
|`Collation`|Określa kolejność sortowania (lub sekwencji sortowania) do użycia podczas wykonywania porównania i kolejność operacji na wartości właściwości.|`String`|  
|`ConcurrencyMode`|Wskazuje, że wartość właściwości powinny być używane do kontroli optymistycznej współbieżności.|Wszystkie właściwości typu pierwotnego|  
|`Default`|Określa wartość domyślną właściwości, jeśli żadna wartość nie jest dostarczony na wystąpienia.|Wszystkie właściwości typu pierwotnego|  
|`FixedLength`|Określa, czy długość wartości właściwości mogą się różnić.|`Binary`, `String`|  
|`MaxLength`|Określa maksymalną długość wartości właściwości.|`Binary`, `String`|  
|`Nullable`|Określa, czy właściwość może mieć wartości null.|Wszystkie właściwości typu pierwotnego|  
|`Precision`|Dla właściwości typu `Decimal`, określa liczbę cyfr, może mieć wartości właściwości. Dla właściwości typu `Time`, `DateTime`, i `DateTimeOffset`, określa liczbę cyfr ułamkowych części sekundy wartości właściwości.|`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,|  
|`Scale`|Określa liczbę cyfr z prawej strony punktu dziesiętnego dla wartości właściwości.|Wartość dziesiętna|  
|`Unicode`|Wskazuje, czy wartość właściwości jest przechowywane w formacie Unicode.|`String`|  
  
## <a name="example"></a>Przykład  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Definiuje następujące CSDL `Book` typu jednostki. Należy pamiętać, że aspekty są zaimplementowane jako atrybuty XML. Wartości aspektu wskazują, że właściwości nie można ustawić wartość null, a `Scale` i `Precision` z `Revision` właściwości każdego ustawiono 29.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
