---
title: C# odwołanie do
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: ccb1463db51510d275b7053955a0257bd4fe621e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422712"
---
# <a name="into-c-reference"></a>into (odwołanie w C#)

Kontekstowe słowo kluczowe `into` może służyć do tworzenia tymczasowego identyfikatora do przechowywania wyników [grupy](group-clause.md), [sprzężenia](join-clause.md) lub [zaznaczania](select-clause.md) do nowego identyfikatora. Ten identyfikator może być generatorem dla dodatkowych poleceń zapytań. W przypadku użycia w klauzuli `group` lub `select` użycie nowego identyfikatora jest czasami określane jako *kontynuacja*.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie słowa kluczowego `into`, aby włączyć tymczasowy identyfikator `fruitGroup`, który ma wnioskowany typ `IGrouping`. Używając identyfikatora, można wywołać metodę <xref:System.Linq.Enumerable.Count%2A> dla każdej grupy i wybrać tylko te grupy, które zawierają dwa lub więcej wyrazów.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

Użycie `into` w klauzuli `group` jest konieczne tylko wtedy, gdy chcesz wykonać dodatkowe operacje zapytań dla każdej grupy. Aby uzyskać więcej informacji, zobacz [klauzula](group-clause.md)Group.

Aby zapoznać się z przykładem użycia `into` w klauzuli `join`, zobacz [Klauzula join](join-clause.md).

## <a name="see-also"></a>Zobacz także

- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [LINQ w C#](../../linq/index.md)
- [group, klauzula](group-clause.md)
