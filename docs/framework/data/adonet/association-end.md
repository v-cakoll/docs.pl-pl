---
title: punkt końcowy skojarzenia
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 489802ca18708e076c0cd5dd380ad1361916ad5f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732360"
---
# <a name="association-end"></a>punkt końcowy skojarzenia
*Punkt końcowy skojarzenia* identyfikuje [Typ jednostki](entity-type.md) na jednym końcu [skojarzenia](association-type.md) i liczbę wystąpień typu jednostki, które mogą istnieć na tym końcu skojarzenia. Punkty końcowe skojarzenia są zdefiniowane jako część skojarzenia; skojarzenie musi mieć dokładnie dwa punkty końcowe skojarzenia. [Właściwości nawigacji](navigation-property.md) umożliwiają nawigowanie z jednego skojarzenia do drugiego.  
  
 Definicja końca skojarzenia zawiera następujące informacje:  
  
- Jeden z typów jednostek uwzględnionych w skojarzeniu. Potrzeb  
  
    > [!NOTE]
    > Dla danego skojarzenia typ jednostki określony dla każdego końca skojarzenia może być taki sam. Spowoduje to utworzenie własnego skojarzenia.  
  
- [Liczebność końcowa skojarzenia](association-end-multiplicity.md) , która wskazuje liczbę wystąpień typu jednostki, które mogą znajdować się na jednym końcu skojarzenia. Liczebność końcowa skojarzenia może mieć wartość jeden (1), zero lub jeden (0.. 1) lub wiele (\*).  
  
- Nazwa punktu końcowego skojarzenia. (opcjonalnie)  
  
- Informacje o operacjach wykonywanych na końcu skojarzenia, takich jak kaskadowo przy usuwaniu. (opcjonalnie)  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z dwoma skojarzeniami: `PublishedBy` i `WrittenBy`. Skojarzenie dla skojarzenia `PublishedBy` jest typem jednostek `Book` i `Publisher`. Liczebność `Publisher` zakończenia to jeden (1), a liczebność `Book` zakończenia ma wiele (\*), co oznacza, że Wydawca publikuje wiele książek, a książka jest publikowana przez jednego wydawcę.  
  
 ![Przykładowy model z trzema typami jednostek](./media/association-end/example-model-three-entity-types.gif)  
  
 ADO.NET Entity Framework używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych. Poniżej definiujemy skojarzenie `PublishedBy` pokazane na powyższym diagramie. Należy zauważyć, że typ, nazwa i liczebność każdego końca skojarzenia są określone przez atrybuty XML (odpowiednio atrybuty `Type`, `Role`i `Multiplicity`). Opcjonalne informacje o operacjach wykonywanych na końcu są określone w elemencie XML (`OnDelete` elementu). W takim przypadku, jeśli zostanie usunięty Wydawca, wszystkie skojarzone książki.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
