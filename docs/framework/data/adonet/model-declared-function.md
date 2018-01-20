---
title: Funkcja zadeklarowana modelu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 37c6b04fbea69f62aaf7bc148ee04ace5a5a349c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="model-declared-function"></a>Funkcja zadeklarowana modelu
A *funkcja zadeklarowana modelu* to funkcja, która jest zadeklarowana w modelu koncepcyjnym, ale nie jest zdefiniowany w modelu koncepcyjnym. Funkcja może być zdefiniowana w środowisku obsługującym lub magazynu. Na przykład funkcja zadeklarowana modelu może być mapowana na funkcję, która jest zdefiniowana w bazie danych, w związku z tym udostępnianie funkcje po stronie serwera w modelu koncepcyjnym.  
  
 Deklaracja funkcji zadeklarowany modelu zawiera następujące informacje:  
  
-   Nazwa funkcji. (Wymagane)  
  
-   Typ zwracanej wartości. (opcjonalnie)  
  
    > [!NOTE]
    >  Jeśli wartość zwrotu nie zostanie określona, typ zwracany jest typ void.  
  
-   Informacje o parametrach, jak nazwa parametru typu. (opcjonalnie)  
  
## <a name="example"></a>Przykład  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. W pliku CSDL, jest jedna implementacja funkcji zadeklarowany modelu [import funkcji](http://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d). Następujący plik CSDL definiuje kontenera jednostek z definicji funkcji importu. Należy pamiętać, że typ zwracany dla funkcji void, ponieważ nie zwracany określono typu.  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
