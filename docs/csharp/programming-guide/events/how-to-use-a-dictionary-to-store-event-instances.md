---
title: 'Porady: użycie słownika do przechowywania wystąpień zdarzeń - C# Programming Guide'
ms.custom: seodec18
ms.date: 03/11/2019
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: f8522e499887398402f63c7788bbc6c6c4f57782
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845280"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>Porady: użycie słownika do przechowywania wystąpień zdarzeń (C# Programming Guide)

Jednym z zastosowań `add` i `remove` niestandardowych metod dostępu zdarzeń jest do udostępnienia wiele zdarzeń, bez przydzielania pola dla każdego zdarzenia, ale zamiast tego za pomocą <xref:System.Collections.Generic.Dictionary%602> wystąpienia do przechowywania wystąpień zdarzeń, tak jak pokazano w poniższym przykładzie. Jest to przydatne tylko wtedy, jeśli typ ma wiele zdarzeń, ale oczekuje się, że większość zdarzeń będzie nie być subskrybowane.

[!code-csharp[csProgGuideEvents#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#9)]

Ta implementacja jest zgodny z zachowaniem dla [Dodawanie i usuwanie obiektów delegowanych](~/_csharplang/spec/delegates.md#delegate-invocation) w C# specyfikacji języka.

Należy pamiętać, że [blokady](../../language-reference/keywords/lock-statement.md) instrukcja jest używane tylko z *dostępu* słownik z programami obsługi zdarzeń. Nie wywołać procedurę obsługi zdarzeń w treści `lock` instrukcji, ponieważ może doprowadzić do zakleszczenia lub blokować rywalizacji o zasoby.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)
- [Delegaty](../../../csharp/programming-guide/delegates/index.md)
