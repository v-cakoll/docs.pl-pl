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
# <a name="global-c-reference"></a><span data-ttu-id="569c5-102">global (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="569c5-102">global (C# Reference)</span></span>

<span data-ttu-id="569c5-103">Kontekstowe słowo kluczowe, gdy występuje przed [operatorem::](../operators/namespace-alias-qualifier.md), odwołuje się do globalnej przestrzeni nazw, która jest domyślną przestrzenią C# nazw dla każdego programu i w przeciwnym razie nie ma nazwy. `global`</span><span class="sxs-lookup"><span data-stu-id="569c5-103">The `global` contextual keyword, when it comes before the [:: operator](../operators/namespace-alias-qualifier.md), refers to the global namespace, which is the default namespace for any C# program and is otherwise unnamed.</span></span> <span data-ttu-id="569c5-104">Aby uzyskać więcej informacji, zobacz [jak: Użyj globalnego aliasu](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="569c5-104">For more information, see [How to: Use the Global Namespace Alias](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span></span>

## <a name="example"></a><span data-ttu-id="569c5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="569c5-105">Example</span></span>

<span data-ttu-id="569c5-106">Poniższy przykład pokazuje, jak używać `global` kontekstowego słowa kluczowego, aby określić, że Klasa `TestApp` jest zdefiniowana w globalnej przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="569c5-106">The following example shows how to use the `global` contextual keyword to specify that the class `TestApp` is defined in the global namespace:</span></span>

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a><span data-ttu-id="569c5-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="569c5-107">See also</span></span>

- [<span data-ttu-id="569c5-108">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="569c5-108">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
