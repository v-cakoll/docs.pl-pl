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
# <a name="global-c-reference"></a><span data-ttu-id="f6cb1-102">global (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f6cb1-102">global (C# Reference)</span></span>

<span data-ttu-id="f6cb1-103">`global` Kontekstowego słowa kluczowego, gdy znajduje się przed [:: operator](../operators/namespace-alias-qualifer.md), odwołuje się do globalnej przestrzeni nazw, która jest domyślny obszar nazw dla dowolnego programu C#, a w przeciwnym razie jest bez nazwy.</span><span class="sxs-lookup"><span data-stu-id="f6cb1-103">The `global` contextual keyword, when it comes before the [:: operator](../operators/namespace-alias-qualifer.md), refers to the global namespace, which is the default namespace for any C# program and is otherwise unnamed.</span></span> <span data-ttu-id="f6cb1-104">Aby uzyskać więcej informacji, zobacz [porady: użycie globalnych aliasów Namespace](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span><span class="sxs-lookup"><span data-stu-id="f6cb1-104">For more information, see [How to: Use the Global Namespace Alias](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span></span>

## <a name="example"></a><span data-ttu-id="f6cb1-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6cb1-105">Example</span></span>

<span data-ttu-id="f6cb1-106">Poniższy przykład pokazuje, jak używać `global` kontekstowe słowo kluczowe, aby określić, że klasa `TestApp` jest zdefiniowany w globalnej przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="f6cb1-106">The following example shows how to use the `global` contextual keyword to specify that the class `TestApp` is defined in the global namespace:</span></span>

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a><span data-ttu-id="f6cb1-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6cb1-107">See also</span></span>

- [<span data-ttu-id="f6cb1-108">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="f6cb1-108">Namespaces</span></span>](../../programming-guide/namespaces/index.md)