---
title: punkt końcowy skojarzenia
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 9d7bd6fa92a4337add18deafbeb5ad28fefcb749
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757440"
---
# <a name="association-end"></a>punkt końcowy skojarzenia
*Końca skojarzenia* identyfikuje [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) na jeden z końców [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) i liczby jednostek wpisz wystąpień, które mogą znajdować się na tym końcu skojarzenia. Punkty końcowe skojarzenia są zdefiniowane jako część skojarzenia; Skojarzenie musi mieć dokładnie dwa punkty końcowe skojarzenia. [Właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) umożliwienia nawigacji z elementu end skojarzenia jednego do drugiego.  
  
 Definicja end skojarzenia zawiera następujące informacje:  
  
-   Jeden z typów jednostek objętego skojarzenia. (Wymagane)  
  
    > [!NOTE]
    >  Dla danego skojarzenia typu jednostki, określony dla każdego końca skojarzenia może być taka sama. Spowoduje to utworzenie skojarzenia własny.  
  
-   [Skojarzenie liczebność zakończenia](../../../../docs/framework/data/adonet/association-end-multiplicity.md) oznacza liczbę wystąpień typów jednostek, które mogą być na jednym końcu skojarzenia. Skojarzenie liczebność zakończenia może mieć wartość jednego (1), zero lub jeden (od 0 do 1) lub wielu (*).  
  
-   Nazwa dla elementu end skojarzenia. (opcjonalnie)  
  
-   Informacje o operacjach wykonywanych na końcu skojarzenia, takich jak cascade przy usuwaniu. (opcjonalnie)  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono modelu koncepcyjnego z dwóch skojarzenia: `PublishedBy` i `WrittenBy`. Punkty końcowe skojarzenia dla `PublishedBy` są skojarzenia `Book` i `Publisher` typy jednostek. Liczebność `Publisher` punkt końcowy jest jeden (1) i liczebność `Book` punkt końcowy jest wiele (*), informujący, że wydawca publikuje wiele książek i książkę są publikowane przez jednego wydawcy.  
  
 ![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET Entity Framework używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Definiuje CSDL poniżej `PublishedBy` skojarzenia pokazano na powyższym diagramie. Należy pamiętać, że typu, nazwy i liczebność każdego końca skojarzenia są określone przez atrybutów XML ( `Type`, `Role`, i `Multiplicity` atrybuty odpowiednio). Dodatkowe informacje o operacji wykonywanych na końcu jest określony w elemencie XML ( `OnDelete` elementu). W takim przypadku usunięcie wydawcy są wszystkie powiązane książek.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
