---
title: skojarzenie i liczebność
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 3f3d8ba9f7e68065024dd3efb599b847496740cd
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738569"
---
# <a name="association-end-multiplicity"></a>skojarzenie i liczebność
*Liczebność końcowa skojarzenia* definiuje liczbę wystąpień [typu jednostki](entity-type.md) , które mogą być na jednym końcu [skojarzenia](association-type.md).  
  
 Liczebność końcowa skojarzenia może mieć jedną z następujących wartości:  
  
- jeden (1): wskazuje, że dokładnie jedno wystąpienie typu jednostki istnieje na końcu skojarzenia.  
  
- zero lub jeden (0.. 1): wskazuje, że na końcu skojarzenia istnieją wystąpienia typu jednostki równe zero lub jeden.  
  
- wiele (\*): wskazuje, że na końcu skojarzenia istnieje zero, jedno lub więcej wystąpień typu jednostki.  
  
 Skojarzenie jest często scharakteryzowane przez jego liczebność końcową skojarzenia. Na przykład, jeśli koniec skojarzenia ma liczebność jeden (1) i wiele (\*), skojarzenie nazywa się skojarzeniem "jeden do wielu". W poniższym przykładzie skojarzenie `PublishedBy` jest skojarzeniem typu jeden-do-wielu (Wydawca publikuje wiele książek, a książka jest publikowana przez jednego wydawcę). Skojarzenie `WrittenBy` jest skojarzeniem wiele-do-wielu (książka może mieć wielu autorów i autor może zapisywać wiele książek).  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z dwoma skojarzeniami: `PublishedBy` i `WrittenBy`. Skojarzenie dla skojarzenia `PublishedBy` jest typem jednostek `Book` i `Publisher`. Liczebność `Publisher` zakończenia to jeden (1), a liczebność zakończenia `Book` ma wiele (\*).  
  
 ![Przykładowy model z trzema typami jednostek](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 ADO.NET Entity Framework używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych. Poniższy obiekt CSDL definiuje skojarzenie `PublishedBy` pokazane na powyższym diagramie:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
