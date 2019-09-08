---
title: typ skojarzenia
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: e75037223b235cf09df0bca85c6a4feb0b340174
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786892"
---
# <a name="association-type"></a>typ skojarzenia
*Typ skojarzenia* (nazywany także skojarzeniem) to podstawowy blok konstrukcyjny do opisywania relacji w Entity Data Model (EDM). W modelu koncepcyjnym skojarzenie reprezentuje relację między dwoma [typami jednostek](entity-type.md) (takimi jak `Customer` i `Order`). W aplikacji wystąpienie skojarzenia reprezentuje określone skojarzenie (takie jak skojarzenie między wystąpieniem `Customer` i `Order`wystąpieniem). Wystąpienia skojarzeń są logicznie pogrupowane w [zestawie skojarzenia](association-set.md).  
  
 Definicja skojarzenia zawiera następujące informacje:  
  
- Unikatowa nazwa. Potrzeb  
  
- Dwa [punkty końcowe skojarzenia](association-end.md), jeden dla każdego typu jednostki w relacji. Potrzeb  
  
    > [!NOTE]
    > Skojarzenie nie może reprezentować relacji między więcej niż dwoma typami jednostek. Skojarzenie może jednak definiować samodzielny przez określenie tego samego typu jednostki dla każdego z jego punktów końcowych skojarzenia.  
  
- [Ograniczenie integralności referencyjnej](referential-integrity-constraint.md). (opcjonalnie)  
  
 Każdy punkt końcowy skojarzenia musi określać [liczebność końcową skojarzenia](association-end-multiplicity.md) , która wskazuje liczbę wystąpień typu jednostki, które mogą znajdować się na jednym końcu skojarzenia. Liczebność końcowa skojarzenia może mieć wartość jednego (1), zero lub jeden (0.. 1) lub wiele (\*). Do wystąpienia typu jednostki na jednym końcu skojarzenia można uzyskać dostęp za poorednictwem [właściwości nawigacji](navigation-property.md) lub kluczy obcych, jeśli są one uwidocznione w typie jednostki. Aby uzyskać więcej informacji, [zobacz Entity Data Model: Klucze](foreign-key-property.md)obce.  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z dwoma skojarzeniami: `PublishedBy` i `WrittenBy`. Skojarzenie `PublishedBy` `Publisher` jest powiązane z typami jednostek i.`Book` Liczebność `Publisher` końca jest jedną (1), a liczebność `Book` końca ma wiele (\*), co oznacza, że Wydawca publikuje wiele książek, a książka jest publikowana przez jednego wydawcę.  
  
 ![Przykładowy model z trzema typami jednostek](./media/association-type/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Poniższy obiekt CSDL definiuje `PublishedBy` skojarzenie pokazane na powyższym diagramie:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
