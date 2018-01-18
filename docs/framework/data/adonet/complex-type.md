---
title: "Typ złożony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6a7fbdace6403d2f1037beff8fe28d7c934d3174
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="complex-type"></a>Typ złożony
A *typu złożonego* szablonem służącym do definiowania właściwości rozbudowane, strukturalnych na [typów jednostek](../../../../docs/framework/data/adonet/entity-type.md) lub na inne typy złożone. Każdy szablon zawiera następujące elementy:  
  
-   Unikatowa nazwa. (Wymagane)  
  
    > [!NOTE]
    >  Nazwa typu złożonego nie może być taka sama jak nazwa typu jednostki w ramach tego samego obszaru nazw.  
  
-   Dane w postaci jednego lub więcej [właściwości](../../../../docs/framework/data/adonet/property.md). (Opcjonalnie).  
  
    > [!NOTE]
    >  Właściwość typu złożonego może być inny typ złożony.  
  
 Typ złożony jest podobny do typu jednostki, w tym typie złożonym może przenosić ładunku danych w formie właściwości typu pierwotnego lub innych typów złożonych. Istnieją jednak niektóre podstawowe różnice między typy jednostek i typów złożonych:  
  
-   Typy złożone nie mają tożsamości i dlatego nie może istnieć niezależnie. Typy złożone może istnieć tylko jako właściwości na typy jednostek i innych typów złożonych.  
  
-   Typy złożone nie może brać udziału w [skojarzenia](../../../../docs/framework/data/adonet/association-type.md). Żadna końca skojarzenia może być typem złożonym i w związku z tym [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) nie może być zdefiniowana dla typów złożonych.  
  
## <a name="example"></a>Przykład  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujący plik CSDL definiuje typ złożony, adres, z właściwością typu pierwotnego `StreetAddress`, `City`, `StateOrProvince`, `Country`, i `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Aby zdefiniować typu złożonego `Address` (powyżej) jako właściwość typu jednostki, należy zadeklarować typ właściwości w definicji typu jednostki. Deklaruje następującego pliku CSDL `Address` właściwości jako typ złożony w ramach typu jednostki (wydawcy):  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
