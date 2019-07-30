---
title: globalne kontekstowe słowo C# kluczowe — odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
ms.openlocfilehash: 9a8c7b5134cc29668aae53e8a3f86ddae4c8263a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627685"
---
# <a name="global-c-reference"></a>global (odwołanie w C#)

Kontekstowe słowo kluczowe, gdy występuje przed [operatorem::](../operators/namespace-alias-qualifier.md), odwołuje się do globalnej przestrzeni nazw, która jest domyślną przestrzenią C# nazw dla każdego programu i w przeciwnym razie nie ma nazwy. `global` Aby uzyskać więcej informacji, zobacz [jak: Użyj globalnego aliasu](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)przestrzeni nazw.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `global` kontekstowego słowa kluczowego, aby określić, że Klasa `TestApp` jest zdefiniowana w globalnej przestrzeni nazw:

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a>Zobacz także

- [Przestrzenie nazw](../../programming-guide/namespaces/index.md)
