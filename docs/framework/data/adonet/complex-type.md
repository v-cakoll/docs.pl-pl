---
title: Typ złożony
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 4e18ecf18399f57769dcdfc77192e72ec47f5df3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555443"
---
# <a name="complex-type"></a>Typ złożony
A *typu złożonego* jest szablon służący do definiowania właściwości zaawansowane, ze strukturą na [typów jednostek](../../../../docs/framework/data/adonet/entity-type.md) lub na inne typy złożone. Każdy szablon zawiera następujące informacje:  
  
-   Unikatowa nazwa. (Wymagane)  
  
    > [!NOTE]
    >  Nazwa typu złożonego nie może być taka sama jak nazwa typu jednostki w ramach tej samej przestrzeni nazw.  
  
-   Dane w postaci jednego lub więcej [właściwości](../../../../docs/framework/data/adonet/property.md). (Opcjonalnie).  
  
    > [!NOTE]
    >  Właściwość typu złożonego, może być innego typu złożonego.  
  
 Typ złożony jest podobny dla typu jednostki, w tym, że typ złożony mogą przenosić ładunek danych w formie właściwości typu pierwotnego lub inne typy złożone. Jednakże istnieją niektóre podstawowe różnice między typy złożone i typy jednostek:  
  
-   Typy złożone nie mają tożsamości i dlatego nie mogą istnieć niezależnie. Typy złożone może istnieć tylko jako właściwości na typy jednostek lub inne typy złożone.  
  
-   Typy złożone nie mogą uczestniczyć w [skojarzenia](../../../../docs/framework/data/adonet/association-type.md). Żadna end elementu association może być typem złożonym i w związku z tym [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) nie można definiować dla typów złożonych.  
  
## <a name="example"></a>Przykład  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujące CSDL definiuje typ złożony, adres, z właściwościami typu pierwotnego `StreetAddress`, `City`, `StateOrProvince`, `Country`, i `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Aby zdefiniować typ złożony `Address` (p. wyżej) jako właściwość typu encji należy zadeklarować typ właściwości w definicji typu jednostki. Deklaruje następujące CSDL `Address` właściwość typu złożonego typu encji (wydawcy):  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Zobacz także
- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
