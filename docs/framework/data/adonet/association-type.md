---
title: typ skojarzenia
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 17465dbec3f5e2896cf755a1f8585734388f54ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948303"
---
# <a name="association-type"></a>typ skojarzenia
*Typ skojarzenia* (nazywany także skojarzeniem) to podstawowy blok konstrukcyjny do opisywania relacji w Entity Data Model (EDM). W modelu koncepcyjnym skojarzenie reprezentuje relację między dwoma [typami jednostek](../../../../docs/framework/data/adonet/entity-type.md) (takimi jak `Customer` i `Order`). W aplikacji wystąpienie skojarzenia reprezentuje określone skojarzenie (takie jak skojarzenie między wystąpieniem `Customer` i `Order`wystąpieniem). Wystąpienia skojarzeń są logicznie pogrupowane w [zestawie skojarzenia](../../../../docs/framework/data/adonet/association-set.md).  
  
 Definicja skojarzenia zawiera następujące informacje:  
  
- Unikatowa nazwa. Potrzeb  
  
- Dwa [punkty końcowe skojarzenia](../../../../docs/framework/data/adonet/association-end.md), jeden dla każdego typu jednostki w relacji. Potrzeb  
  
    > [!NOTE]
    > Skojarzenie nie może reprezentować relacji między więcej niż dwoma typami jednostek. Skojarzenie może jednak definiować samodzielny przez określenie tego samego typu jednostki dla każdego z jego punktów końcowych skojarzenia.  
  
- [Ograniczenie integralności referencyjnej](../../../../docs/framework/data/adonet/referential-integrity-constraint.md). (opcjonalnie)  
  
 Każdy punkt końcowy skojarzenia musi określać [liczebność końcową skojarzenia](../../../../docs/framework/data/adonet/association-end-multiplicity.md) , która wskazuje liczbę wystąpień typu jednostki, które mogą znajdować się na jednym końcu skojarzenia. Liczebność końcowa skojarzenia może mieć wartość jednego (1), zero lub jeden (0.. 1) lub wiele (\*). Do wystąpienia typu jednostki na jednym końcu skojarzenia można uzyskać dostęp za poorednictwem [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) lub kluczy obcych, jeśli są one uwidocznione w typie jednostki. Aby uzyskać więcej informacji, [zobacz Entity Data Model: Klucze](../../../../docs/framework/data/adonet/foreign-key-property.md)obce.  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z dwoma skojarzeniami: `PublishedBy` i `WrittenBy`. Skojarzenie `PublishedBy` `Publisher` jest powiązane z typami jednostek i.`Book` Liczebność `Publisher` końca jest jedną (1), a liczebność `Book` końca ma wiele (\*), co oznacza, że Wydawca publikuje wiele książek, a książka jest publikowana przez jednego wydawcę.  
  
 ![Przykładowy model z trzema typami jednostek](./media/association-type/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Poniższy obiekt CSDL definiuje `PublishedBy` skojarzenie pokazane na powyższym diagramie:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
