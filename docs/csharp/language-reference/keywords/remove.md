---
title: Usuń kontekstowego słowa kluczowego - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: fc6f310e17841349d476f35214ac17100e81d76f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236729"
---
# <a name="remove-c-reference"></a>remove (odwołanie w C#)

`remove` Kontekstowe słowo kluczowe jest używane do definiowania metody dostępu zdarzeń niestandardowych, które jest wywoływane, gdy kod klienta, który anuluje subskrypcje ze swojej [zdarzeń](event.md). Jeśli podasz niestandardowe `remove` dostępu, należy również podać [Dodaj](add.md) metody dostępu.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano zdarzenia niestandardowe [Dodaj](add.md) i `remove` metod dostępu. Pełny przykład można znaleźć [jak:  Zdarzenia implementowania interfejsu](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Zazwyczaj nie trzeba podać własne niestandardowych metod dostępu zdarzeń. Metody dostępu, które są automatycznie generowane przez kompilator przy deklarowaniu zdarzenie są wystarczające dla większości scenariuszy.

## <a name="see-also"></a>Zobacz także

- [Zdarzenia](../../programming-guide/events/index.md)