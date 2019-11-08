---
title: typ złożony
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: e21ca90a7be8f2bd9be9483c66a1e95e6ba1bee2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738546"
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
 [ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych. Poniższy identyfikator CSDL definiuje typ złożony, adres z właściwościami typu pierwotnego `StreetAddress`, `City`, `StateOrProvince`, `Country`i `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Aby zdefiniować typ złożony `Address` (powyżej) jako właściwość typu jednostki, należy zadeklarować typ właściwości w definicji typu jednostki. Następujący CSDL deklaruje Właściwość `Address` jako typ złożony dla typu jednostki (wydawca):  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
