---
title: Właściwość nawigacji — ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: 6729b22dbc012d5ccfabd64cd83b710833fe1b9d
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857947"
---
# <a name="navigation-property"></a>Właściwość nawigacji

A *właściwość nawigacji* jest opcjonalną właściwością na [typu jednostki](entity-type.md) umożliwiającą nawigacji z jednego [zakończenia](association-end.md) z [skojarzenia](association-type.md) do Data zakończenia. W odróżnieniu od innych [właściwości](property.md), właściwości nawigacji nie zawierają danych.

Definicja właściwości nawigacji obejmuje następujące funkcje:

- Nazwa. (Wymagane)

- Skojarzenie go przechodzi. (Wymagane)

- Końcach asocjacji, prowadzącego go. (Wymagane)

Należy pamiętać, że właściwości nawigacji są opcjonalne na obu typów jednostek na końcach asocjacji. Jeśli zdefiniujesz właściwości nawigacji na jednym typie jednostek na końcu asocjacji, ma Zdefiniuj właściwość nawigacji typu jednostki na drugim końcu skojarzenia.

Typ danych właściwości nawigacji jest określana przez [liczebność](association-end-multiplicity.md) jego zdalnego [end skojarzenia](association-end.md). Na przykład, załóżmy, że właściwość nawigacji, `OrdersNavProp`, istnieje na `Customer` typu jednostki i przechodzi skojarzenia typu jeden do wielu między `Customer` i `Order`. Ponieważ punkt końcowy skojarzenia zdalnego dla właściwości nawigacji ma liczebność wielu (\*), jego typ danych to kolekcja (z `Order`). Podobnie, jeśli właściwość nawigacji, `CustomerNavProp`, istnieje na `Order` typu jednostki, będzie jego typu danych `Customer`, ponieważ liczebność drugim końcu jest jeden (1).

## <a name="example"></a>Przykład

Poniższy diagram przedstawia modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`. Właściwości nawigacji `Publisher` i `Authors`, są zdefiniowane w typie jednostki książki. Właściwość nawigacji `Books` jest zdefiniowany w obu typ jednostki wydawcy i `Author` typu jednostki.

![Model przy użyciu właściwości nawigacji](/media/modelwithnavprops.gif "ModelWithNavProps")

[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych. Definiuje następujące CSDL `Book` typu jednostki, które pokazano na powyższym diagramie:

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

Należy zwrócić uwagę na to, że atrybuty XML są używane do przekazywania informacji niezbędnych do definiowania właściwości nawigacji: Ten atrybut `Name` zawiera nazwę właściwości, `Relationship` zawiera nazwę skojarzenia powoduje przejście, i `FromRole` i `ToRole` zawierają końcach asocjacji.

## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
- [Relacje, właściwości nawigacji i kluczy obcych](/ef/ef6/fundamentals/relationships)
