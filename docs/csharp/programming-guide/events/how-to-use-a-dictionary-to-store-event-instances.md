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
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="a5994-102">Porady: użycie słownika do przechowywania wystąpień zdarzeń (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="a5994-102">How to: use a dictionary to store event instances (C# Programming Guide)</span></span>

<span data-ttu-id="a5994-103">Jednym z zastosowań `add` i `remove` niestandardowych metod dostępu zdarzeń jest do udostępnienia wiele zdarzeń, bez przydzielania pola dla każdego zdarzenia, ale zamiast tego za pomocą <xref:System.Collections.Generic.Dictionary%602> wystąpienia do przechowywania wystąpień zdarzeń, tak jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a5994-103">One use for the `add` and `remove` custom event accessors is to expose many events without allocating a field for each event, but instead using a <xref:System.Collections.Generic.Dictionary%602> instance to store the event instances, as the example below demonstrates.</span></span> <span data-ttu-id="a5994-104">Jest to przydatne tylko wtedy, jeśli typ ma wiele zdarzeń, ale oczekuje się, że większość zdarzeń będzie nie być subskrybowane.</span><span class="sxs-lookup"><span data-stu-id="a5994-104">This is only useful if a type has many events, but you expect that most of the events will not be subscribed to.</span></span>

[!code-csharp[csProgGuideEvents#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#9)]

<span data-ttu-id="a5994-105">Ta implementacja jest zgodny z zachowaniem dla [Dodawanie i usuwanie obiektów delegowanych](~/_csharplang/spec/delegates.md#delegate-invocation) w C# specyfikacji języka.</span><span class="sxs-lookup"><span data-stu-id="a5994-105">This implementation conforms to the behavior for [adding and removing delegates](~/_csharplang/spec/delegates.md#delegate-invocation) in the C# language specification.</span></span>

<span data-ttu-id="a5994-106">Należy pamiętać, że [blokady](../../language-reference/keywords/lock-statement.md) instrukcja jest używane tylko z *dostępu* słownik z programami obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a5994-106">Note that the [lock](../../language-reference/keywords/lock-statement.md) statement is used only to *access* the dictionary with event handlers.</span></span> <span data-ttu-id="a5994-107">Nie wywołać procedurę obsługi zdarzeń w treści `lock` instrukcji, ponieważ może doprowadzić do zakleszczenia lub blokować rywalizacji o zasoby.</span><span class="sxs-lookup"><span data-stu-id="a5994-107">Don't invoke an event handler inside the body of the `lock` statement, as it could lead to deadlocks or lock contention.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5994-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5994-108">See also</span></span>

- [<span data-ttu-id="a5994-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a5994-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a5994-110">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a5994-110">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="a5994-111">Delegaty</span><span class="sxs-lookup"><span data-stu-id="a5994-111">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
