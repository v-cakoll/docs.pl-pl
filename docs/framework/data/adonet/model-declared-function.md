---
title: Funkcja zadeklarowana modelu
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: f92bdfedaefca7182b5de72abae9852965d83ff7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511518"
---
# <a name="model-declared-function"></a>Funkcja zadeklarowana modelu
A *funkcja zadeklarowana modelu* jest funkcją, która jest zadeklarowana w modelu koncepcyjnym, ale nie jest zdefiniowany w tym modelu koncepcyjnego. Funkcja może być zdefiniowana w środowisku hostingu lub magazynu. Na przykład funkcja zadeklarowana modelu może być mapowana do funkcji, która jest zdefiniowana w bazie danych, w związku z tym udostępnianie funkcje po stronie serwera w modelu koncepcyjnym.  
  
 Deklaracja funkcji zadeklarowana modelu zawiera następujące informacje:  
  
-   Nazwa funkcji. (Wymagane)  
  
-   Typ wartości zwracanej. (opcjonalnie)  
  
    > [!NOTE]
    >  Jeśli żadna wartość zwracana jest określony, zwracany typ jest typ void.  
  
-   Informacje o parametrach, takie jak nazwa parametru i typu. (opcjonalnie)  
  
## <a name="example"></a>Przykład  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. W CSDL, jest jedna implementacja funkcja zadeklarowana modelu [funkcji importu](https://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d). Następujące CSDL definiuje kontener jednostek, definicje importu funkcji. Należy zauważyć, że zwracany typ funkcji jest nieważne, ponieważ określono bez zwrotu typu.  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
