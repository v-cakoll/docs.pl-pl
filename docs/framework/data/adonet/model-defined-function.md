---
title: funkcja zdefiniowana przez model
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 05a44e86a118b649490cde849c8ca2c2bb0d2f15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934520"
---
# <a name="model-defined-function"></a>funkcja zdefiniowana przez model
*Funkcja zdefiniowana przez model* jest funkcją zdefiniowaną w modelu koncepcyjnym. Treść funkcji zdefiniowanej przez model jest wyrażona w [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), która umożliwia określenie, że funkcja ma być wyrażona niezależnie od zasad lub języków obsługiwanych w źródle danych.  
  
 Definicja dla funkcji zdefiniowanej przez model zawiera następujące informacje:  
  
- Nazwa funkcji. Potrzeb  
  
- Typ wartości zwracanej. (opcjonalnie)  
  
    > [!NOTE]
    > Jeśli nie określono typu zwracanego, wartość zwracana to void.  
  
- Informacje o parametrach. (opcjonalnie)  
  
- Wyrażenie [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) definiujące treść funkcji.  
  
 Należy zauważyć, że funkcje zdefiniowane przez model nie obsługują parametrów wyjściowych. To ograniczenie jest stosowane, aby można było składać funkcje zdefiniowane przez model.  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`.  
  
 ![Zrzut ekranu, który pokazuje model z datą opublikowaną.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Poniższy CSDL definiuje funkcję w modelu koncepcyjnym, która zwraca liczbę lat od momentu opublikowania wystąpienia `Book` obiektu (na diagramie powyżej).  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
- [Entity Data Model: Typy danych pierwotnych](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
