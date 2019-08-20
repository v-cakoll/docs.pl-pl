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
ms.openlocfilehash: dc1e2ee004c21bb3d05155eec3e42ea80bf641a1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608639"
---
# <a name="into-c-reference"></a>into (odwołanie w C#)

Kontekstowe słowo kluczowe może służyć do tworzenia tymczasowego identyfikatora do przechowywania wyników [grupy](group-clause.md), sprzężenia lub [zaznaczania](select-clause.md) do nowego identyfikatora. [](join-clause.md) `into` Ten identyfikator może być generatorem dla dodatkowych poleceń zapytań. W przypadku użycia w `group` klauzuli `select` or, użycie nowego identyfikatora jest czasami określane jako *kontynuacja*.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `into` słowa kluczowego, aby włączyć tymczasowy identyfikator `fruitGroup` , który ma wnioskowany typ `IGrouping`. Używając identyfikatora, można wywołać <xref:System.Linq.Enumerable.Count%2A> metodę dla każdej grupy i wybrać tylko te grupy, które zawierają dwa lub więcej wyrazów.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

`into` Użycie`group` w klauzuli jest wymagane tylko wtedy, gdy chcesz wykonać dodatkowe operacje na zapytania dla każdej grupy. Aby uzyskać więcej informacji, zobacz artykuł [kluzula group](group-clause.md).

Aby zapoznać się z przykładem użycia `into` `join` w klauzuli, zobacz [Klauzula join](join-clause.md).

## <a name="see-also"></a>Zobacz także

- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [Wyrażenia zapytania LINQ](../../programming-guide/linq-query-expressions/index.md)
- [group, klauzula](group-clause.md)
