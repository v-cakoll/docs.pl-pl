---
title: punkt końcowy skojarzenia
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 575157cd1d125d3315e1859aad72cc8b08d8b4cf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932201"
---
# <a name="association-end"></a>punkt końcowy skojarzenia
*Punkt końcowy skojarzenia* identyfikuje [Typ jednostki](../../../../docs/framework/data/adonet/entity-type.md) na jednym końcu [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) i liczbę wystąpień typu jednostki, które mogą istnieć na tym końcu skojarzenia. Punkty końcowe skojarzenia są zdefiniowane jako część skojarzenia; skojarzenie musi mieć dokładnie dwa punkty końcowe skojarzenia. [Właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) umożliwiają nawigowanie z jednego skojarzenia do drugiego.  
  
 Definicja końca skojarzenia zawiera następujące informacje:  
  
- Jeden z typów jednostek uwzględnionych w skojarzeniu. Potrzeb  
  
    > [!NOTE]
    > Dla danego skojarzenia typ jednostki określony dla każdego końca skojarzenia może być taki sam. Spowoduje to utworzenie własnego skojarzenia.  
  
- [Liczebność końcowa skojarzenia](../../../../docs/framework/data/adonet/association-end-multiplicity.md) , która wskazuje liczbę wystąpień typu jednostki, które mogą znajdować się na jednym końcu skojarzenia. Liczebność końcowa skojarzenia może mieć wartość jednego (1), zero lub jeden (0.. 1) lub wiele (\*).  
  
- Nazwa punktu końcowego skojarzenia. (opcjonalnie)  
  
- Informacje o operacjach wykonywanych na końcu skojarzenia, takich jak kaskadowo przy usuwaniu. (opcjonalnie)  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z dwoma skojarzeniami: `PublishedBy` i `WrittenBy`. Skojarzenie `PublishedBy` `Publisher` jest powiązane z typami jednostek i.`Book` Liczebność `Publisher` końca jest jedną (1), a liczebność `Book` końca ma wiele (\*), co oznacza, że Wydawca publikuje wiele książek, a książka jest publikowana przez jednego wydawcę.  
  
 ![Przykładowy model z trzema typami jednostek](./media/association-end/example-model-three-entity-types.gif)  
  
 ADO.NET Entity Framework używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Poniżej definiujemy `PublishedBy` skojarzenie pokazane na powyższym diagramie. Należy zauważyć, że typ, nazwa i liczebność każdego końca skojarzenia są określone przez atrybuty XML ( `Type` `Role`odpowiednio atrybuty, i `Multiplicity` ). Opcjonalne informacje o operacjach wykonywanych na końcu są określone w elemencie XML ( `OnDelete` elementu). W takim przypadku, jeśli zostanie usunięty Wydawca, wszystkie skojarzone książki.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
