---
title: Usuń kontekstowe słowo C# kluczowe — odwołanie
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 8ea3ea1910e28c03b2a894c64415cb2ccff942d0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713147"
---
# <a name="remove-c-reference"></a>remove (odwołanie w C#)

`remove` kontekstowe słowo kluczowe jest używane do definiowania niestandardowego akcesora zdarzeń, który jest wywoływany, gdy kod klienta anulował subskrypcję ze [zdarzenia](event.md). W przypadku podania niestandardowej metody dostępu `remove` należy również podać metodę dostępu [Dodaj](add.md) .

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano zdarzenie z niestandardowymi dostępem [Dodawanie](add.md) i `remove`. Pełny przykład można znaleźć w temacie [jak zaimplementować zdarzenia interfejsu](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Zazwyczaj nie trzeba podawać własnych niestandardowych metod dostępu do zdarzeń. Metody dostępu, które są generowane automatycznie przez kompilator podczas deklarowania zdarzenia, są wystarczające dla większości scenariuszy.

## <a name="see-also"></a>Zobacz także

- [Zdarzenia](../../programming-guide/events/index.md)
