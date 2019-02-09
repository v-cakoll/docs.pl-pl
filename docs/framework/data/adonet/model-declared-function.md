---
title: Funkcja zadeklarowana modelu
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: 31efbab4b8323ff8cec9498fa20fa40b1efb819e
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904074"
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
 [ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych. W CSDL, jedna implementacja funkcja zadeklarowana modelu jest importowanie funkcji (przy użyciu [FunctionImport element](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)). Następujące CSDL definiuje kontener jednostek, definicje importu funkcji. Należy zauważyć, że zwracany typ funkcji jest nieważne, ponieważ określono bez zwrotu typu.  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>Zobacz także
- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
