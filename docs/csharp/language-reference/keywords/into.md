---
title: do - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: f0f5ff1e56a65e83385f814df2fadd957f53561e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713625"
---
# <a name="into-c-reference"></a>into (odwołanie w C#)

Kontekstowe `into` słowo kluczowe może służyć do utworzenia tymczasowego identyfikatora do przechowywania wyników [grupy,](group-clause.md) [sprzężenia](join-clause.md) lub [wybierz](select-clause.md) klauzulę w nowym identyfikatorze. Ten identyfikator może być generatorem dla dodatkowych poleceń kwerendy. W przypadku `group` użycia `select` w lub klauzuli, użycie nowego identyfikatora jest czasami określane jako *kontynuacja*.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `into` użycie słowa kluczowego `fruitGroup` w celu włączenia tymczasowego identyfikatora, który ma wywnioskowany typ `IGrouping`. Za pomocą identyfikatora, można wywołać <xref:System.Linq.Enumerable.Count%2A> metodę w każdej grupie i wybrać tylko te grupy, które zawierają dwa lub więcej słów.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

Użycie `into` w klauzuli `group` jest konieczne tylko wtedy, gdy chcesz wykonać dodatkowe operacje kwerendy na każdej grupie. Aby uzyskać więcej informacji, zobacz [klauzulę group](group-clause.md).

Na przykład użycia `into` w klauzuli, `join` zobacz join [klauzuli](join-clause.md).

## <a name="see-also"></a>Zobacz też

- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [LINQ w C#](../../linq/index.md)
- [group, klauzula](group-clause.md)
