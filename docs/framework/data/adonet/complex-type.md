---
title: typ złożony
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: fac25ace69938e1245200e10285f4460ac216780
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948734"
---
# <a name="complex-type"></a>typ złożony
*Typ złożony* to szablon służący do definiowania bogatych, strukturalnych właściwości w [typach jednostek](../../../../docs/framework/data/adonet/entity-type.md) lub w innych typach złożonych. Każdy szablon zawiera następujące elementy:  
  
- Unikatowa nazwa. Potrzeb  
  
    > [!NOTE]
    > Nazwa typu złożonego nie może być taka sama jak nazwa typu jednostki w obrębie tej samej przestrzeni nazw.  
  
- Dane w postaci jednej lub wielu [Właściwości](../../../../docs/framework/data/adonet/property.md). (Opcjonalnie).  
  
    > [!NOTE]
    > Właściwość typu złożonego może być innym typem złożonym.  
  
 Typ złożony jest podobny do typu jednostki, w którym typ złożony może przenosić ładunek danych w postaci właściwości typu pierwotnego lub innych typów złożonych. Istnieją jednak pewne kluczowe różnice między typami złożonymi i typami jednostek:  
  
- Typy złożone nie mają tożsamości i w związku z tym nie mogą istnieć niezależnie. Typy złożone mogą istnieć tylko jako właściwości typów jednostek lub innych typów złożonych.  
  
- Typy złożone nie mogą uczestniczyć [](../../../../docs/framework/data/adonet/association-type.md)w skojarzeniach. Żadne zakończenie skojarzenia nie może być typem złożonym, dlatego [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) nie mogą być zdefiniowane w typach złożonych.  
  
## <a name="example"></a>Przykład  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujący CSDL definiuje typ złożony, adres, z `StreetAddress`właściwościami typu pierwotnego, `City`, `StateOrProvince` `Country`,, i `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Aby zdefiniować typ `Address` złożony (powyżej) jako właściwość typu jednostki, należy zadeklarować typ właściwości w definicji typu jednostki. Następujący CSDL deklaruje `Address` właściwość jako typ złożony dla typu jednostki (wydawca):  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
