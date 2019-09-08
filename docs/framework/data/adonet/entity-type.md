---
title: typ jednostki
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: efd3ea0972148e885d4b22b49040640539bb28cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795120"
---
# <a name="entity-type"></a>typ jednostki
*Typ jednostki* jest podstawowym blokiem konstrukcyjnym opisującym strukturę danych z Entity Data Model (EDM). W modelu koncepcyjnym typ jednostki reprezentuje strukturę koncepcji najwyższego poziomu, takich jak klienci lub zamówienia. Typ jednostki to szablon wystąpień typu jednostki. Każdy szablon zawiera następujące informacje:  
  
- Unikatowa nazwa. (Wymagane).  
  
- [Klucz jednostki](entity-key.md) zdefiniowany przez jedną lub więcej właściwości. (Wymagane).  
  
- Dane w postaci [Właściwości](property.md). (Opcjonalnie).  
  
- [Właściwości nawigacji](navigation-property.md) , które umożliwiają nawigację z jednego [końca](association-end.md) [skojarzenia](association-type.md) z drugim. (opcjonalnie)  
  
 W aplikacji wystąpienie typu jednostki reprezentuje określony obiekt (na przykład konkretny klient lub zamówienie). Każde wystąpienie typu jednostki musi mieć unikatowy [klucz jednostki](entity-key.md) w ramach [zestawu jednostek](entity-set.md).  
  
 Dwa wystąpienia typu jednostki są uważane za równe tylko wtedy, gdy są one tego samego typu, a wartości ich kluczy jednostek są takie same.  
  
## <a name="example"></a>Przykład  
 Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`:  
  
 ![Przykładowy model z trzema typami jednostek](./media/entity-type/example-model-three-entity-types.gif)  
  
 Należy zauważyć, że właściwości każdego typu jednostki, które tworzą swój klucz jednostki, są oznaczane "(kluczem)".  
  
 [ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Poniższy `Book` obiekt CSDL definiuje typ jednostki przedstawiony na poniższym diagramie:  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
- [aspekt](facet.md)
