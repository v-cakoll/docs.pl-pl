---
title: Global — słowo kluczowe kontekstowe - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
ms.openlocfilehash: b9273feb38b14dce61facc0f59b0890c431b9a7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661519"
---
# <a name="global-c-reference"></a><span data-ttu-id="052b3-102">global (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="052b3-102">global (C# Reference)</span></span>

<span data-ttu-id="052b3-103">`global` Kontekstowego słowa kluczowego, gdy znajduje się przed [:: operator](../operators/namespace-alias-qualifer.md), odwołuje się do globalnej przestrzeni nazw, która jest domyślny obszar nazw dla dowolnego programu C#, a w przeciwnym razie jest bez nazwy.</span><span class="sxs-lookup"><span data-stu-id="052b3-103">The `global` contextual keyword, when it comes before the [:: operator](../operators/namespace-alias-qualifer.md), refers to the global namespace, which is the default namespace for any C# program and is otherwise unnamed.</span></span> <span data-ttu-id="052b3-104">Aby uzyskać więcej informacji, zobacz [jak: Użycie globalnych aliasów Namespace](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span><span class="sxs-lookup"><span data-stu-id="052b3-104">For more information, see [How to: Use the Global Namespace Alias](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span></span>

## <a name="example"></a><span data-ttu-id="052b3-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="052b3-105">Example</span></span>

<span data-ttu-id="052b3-106">Poniższy przykład pokazuje, jak używać `global` kontekstowe słowo kluczowe, aby określić, że klasa `TestApp` jest zdefiniowany w globalnej przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="052b3-106">The following example shows how to use the `global` contextual keyword to specify that the class `TestApp` is defined in the global namespace:</span></span>

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a><span data-ttu-id="052b3-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="052b3-107">See also</span></span>

- [<span data-ttu-id="052b3-108">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="052b3-108">Namespaces</span></span>](../../programming-guide/namespaces/index.md)