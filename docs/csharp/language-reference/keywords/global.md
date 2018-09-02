---
title: globalne kontekstowe słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
ms.openlocfilehash: 837245e31a9a795aa2f13cfc6c33fefb6402801d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401077"
---
# <a name="global-c-reference"></a>global (odwołanie w C#)

`global` Kontekstowego słowa kluczowego, gdy znajduje się przed [:: operator](../operators/namespace-alias-qualifer.md), odwołuje się do globalnej przestrzeni nazw, która jest domyślny obszar nazw dla dowolnego programu C#, a w przeciwnym razie jest bez nazwy. Aby uzyskać więcej informacji, zobacz [porady: użycie globalnych aliasów Namespace](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `global` kontekstowe słowo kluczowe, aby określić, że klasa `TestApp` jest zdefiniowany w globalnej przestrzeni nazw:

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a>Zobacz także

- [Przestrzenie nazw](../../programming-guide/namespaces/index.md)