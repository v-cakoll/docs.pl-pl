---
title: Właściwość nawigacji — ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: afb2043abf70fa92ea7cdf8d1e8246d5cdfdba74
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738388"
---
# <a name="navigation-property"></a>Właściwość nawigacji

*Właściwość nawigacji* jest opcjonalną właściwością [typu jednostki](entity-type.md) , która umożliwia nawigację z jednego [końca](association-end.md) [skojarzenia](association-type.md) z drugim. W przeciwieństwie do innych [Właściwości](property.md), właściwości nawigacji nie zawierają danych.

Definicja właściwości nawigacji obejmuje następujące elementy:

- Nazwa. Potrzeb

- Skojarzone skojarzenie. Potrzeb

- Koniec skojarzenia, które przechodzi. Potrzeb

Należy zauważyć, że właściwości nawigacji są opcjonalne na obu typach jednostek na końcu skojarzenia. Jeśli zdefiniujesz właściwość nawigacji na jednym typie jednostki na końcu skojarzenia, nie musisz definiować właściwości nawigacji dla typu jednostki na drugim końcu skojarzenia.

Typ danych właściwości nawigacji jest określany przez [liczebność](association-end-multiplicity.md) jego zdalnego [skojarzenia](association-end.md). Załóżmy na przykład, że właściwość nawigacji, `OrdersNavProp`, istnieje w typie jednostki `Customer` i przechodzi do skojarzenia jeden-do-wielu między `Customer` i `Order`. Ze względu na to, że zdalne skojarzenie dla właściwości nawigacji ma liczebność wielu (\*), jego typ danych jest kolekcją (`Order`). Podobnie, jeśli właściwość nawigacji, `CustomerNavProp`, istnieje w typie jednostki `Order`, jego typ danych będzie `Customer`, ponieważ liczebność elementu zdalnego kończy wynosi jeden (1).

## <a name="example"></a>Przykład

Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`. Właściwości nawigacji, `Publisher` i `Authors`są zdefiniowane w typie jednostki książki. Właściwość nawigacji `Books` jest zdefiniowana zarówno dla typu jednostki wydawcy, jak i typu jednostki `Author`.

 ![Diagram przedstawiający model koncepcyjny z trzema typami jednostek.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych. Następujący identyfikator CSDL definiuje typ jednostki `Book` przedstawiony na poniższym diagramie:

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

Należy zauważyć, że atrybuty XML są używane do przekazywania informacji niezbędnych do zdefiniowania właściwości nawigacji: atrybut `Name` zawiera nazwę właściwości, `Relationship` zawiera nazwę elementu, do którego prowadzi Nawigacja, a `FromRole` i `ToRole` zawierają koniec skojarzenia.

## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
- [Relacje, właściwości nawigacji i klucze obce](/ef/ef6/fundamentals/relationships)
