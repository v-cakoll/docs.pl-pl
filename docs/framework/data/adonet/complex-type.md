---
title: typ złożony
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 0d9b8efd08cc0dfba5b26a70773b614b0d63d74f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786745"
---
# <a name="complex-type"></a>typ złożony
*Typ złożony* to szablon służący do definiowania bogatych, strukturalnych właściwości w [typach jednostek](entity-type.md) lub w innych typach złożonych. Każdy szablon zawiera następujące elementy:  
  
- Unikatowa nazwa. Potrzeb  
  
    > [!NOTE]
    > Nazwa typu złożonego nie może być taka sama jak nazwa typu jednostki w obrębie tej samej przestrzeni nazw.  
  
- Dane w postaci jednej lub wielu [Właściwości](property.md). (Opcjonalnie).  
  
    > [!NOTE]
    > Właściwość typu złożonego może być innym typem złożonym.  
  
 Typ złożony jest podobny do typu jednostki, w którym typ złożony może przenosić ładunek danych w postaci właściwości typu pierwotnego lub innych typów złożonych. Istnieją jednak pewne kluczowe różnice między typami złożonymi i typami jednostek:  
  
- Typy złożone nie mają tożsamości i w związku z tym nie mogą istnieć niezależnie. Typy złożone mogą istnieć tylko jako właściwości typów jednostek lub innych typów złożonych.  
  
- Typy złożone nie mogą uczestniczyć w [skojarzeniach](association-type.md). Żadne zakończenie skojarzenia nie może być typem złożonym, dlatego [właściwości nawigacji](navigation-property.md) nie mogą być zdefiniowane w typach złożonych.  
  
## <a name="example"></a>Przykład  
 [ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Następujący CSDL definiuje typ złożony, adres, z `StreetAddress`właściwościami typu pierwotnego, `City`, `StateOrProvince` `Country`,, i `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Aby zdefiniować typ `Address` złożony (powyżej) jako właściwość typu jednostki, należy zadeklarować typ właściwości w definicji typu jednostki. Następujący CSDL deklaruje `Address` właściwość jako typ złożony dla typu jednostki (wydawca):  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
