---
title: into (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: 6d46ae67dd84650172125c62ea70dc109671a89b
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934769"
---
# <a name="into-c-reference"></a>into (odwołanie w C#)

`into` Kontekstowe słowo kluczowe może służyć do tworzenia tymczasowych identyfikatora do przechowywania wyników [grupy](group-clause.md), [sprzężenia](join-clause.md) lub [wybierz](select-clause.md) klauzuli na nowy identyfikator. Sam ten identyfikator może być generator zapytania dodatkowych poleceń. Gdy są używane w `group` lub `select` klauzuli użytkowania nowy identyfikator jest czasami określane jako *kontynuacji*.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `into` — słowo kluczowe, aby włączyć identyfikator tymczasowy `fruitGroup` mającego wnioskowany typ `IGrouping`. Za pomocą identyfikatora, można wywołać <xref:System.Linq.Enumerable.Count%2A> metody na każdym grupy i wybierz tylko te grupy, które zawiera dwa lub więcej słów.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

Korzystanie z `into` w `group` klauzula jest konieczne tylko wtedy, gdy chcesz wykonać operacje zapytań dodatkowe w każdej grupie. Aby uzyskać więcej informacji, zobacz artykuł [kluzula group](group-clause.md).

Na przykład użycie `into` w `join` klauzuli, zobacz [klauzuli join](join-clause.md).

## <a name="see-also"></a>Zobacz także

- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)  
- [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [group, klauzula](group-clause.md)  