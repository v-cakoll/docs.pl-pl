---
title: usuwanie kontekstowe słowo kluczowe — Odwołanie C#
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 8ea3ea1910e28c03b2a894c64415cb2ccff942d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713147"
---
# <a name="remove-c-reference"></a>remove (odwołanie w C#)

Kontekstowe `remove` słowo kluczowe służy do definiowania niestandardowego akcesora zdarzeń, który jest wywoływany, gdy kod klienta anuluje subskrypcję [ze zdarzenia](event.md). Jeśli podasz `remove` niestandardowy akcesor, należy również podać [add](add.md) akcesor.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono zdarzenie `remove` z niestandardowymi [add](add.md) i akcesorami. Aby uzyskać pełny przykład, zobacz [Jak zaimplementować zdarzenia interfejsu](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Zazwyczaj nie trzeba podać własne niestandardowe akcesory zdarzeń. Akcesory, które są automatycznie generowane przez kompilator podczas deklarowania zdarzenia są wystarczające dla większości scenariuszy.

## <a name="see-also"></a>Zobacz też

- [Zdarzenia](../../programming-guide/events/index.md)
