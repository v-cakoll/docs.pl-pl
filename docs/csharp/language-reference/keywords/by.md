---
title: według kontekstowego słowa C# kluczowego — odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- by
- by_CSharpKeyword
helpviewer_keywords:
- by keyword [C#]
ms.assetid: efe6f0e3-be40-4df2-a144-c7db968ae052
ms.openlocfilehash: 23daf2aaf5d9456c76c5b2ac889243b1ed31b077
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602226"
---
# <a name="by-c-reference"></a><span data-ttu-id="97241-102">by (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="97241-102">by (C# Reference)</span></span>

<span data-ttu-id="97241-103">Kontekstowe słowo kluczowe `by` jest używane w klauzuli `group` w wyrażeniu zapytania, co pozwala określić, w jaki sposób powinny zostać zgrupowane zwracane elementy.</span><span class="sxs-lookup"><span data-stu-id="97241-103">The `by` contextual keyword is used in the `group` clause in a query expression to specify how the returned items should be grouped.</span></span> <span data-ttu-id="97241-104">Aby uzyskać więcej informacji, zobacz artykuł [kluzula group](./group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="97241-104">For more information, see [group clause](./group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="97241-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="97241-105">Example</span></span>

<span data-ttu-id="97241-106">W poniższym przykładzie przedstawiono użycie kontekstowego słowa kluczowego `by` w klauzuli `group`, aby sprecyzować, że studenci powinni zostać pogrupowani według pierwszej litery nazwiska.</span><span class="sxs-lookup"><span data-stu-id="97241-106">The following example shows the use of the `by` contextual keyword in a `group` clause to specify that the students should be grouped according to the first letter of the last name of each student.</span></span>

[!code-csharp[csrefKeywordsContextual#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#10)]

## <a name="see-also"></a><span data-ttu-id="97241-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97241-107">See also</span></span>

- [<span data-ttu-id="97241-108">Wyrażenia zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="97241-108">LINQ Query Expressions</span></span>](../../programming-guide/linq-query-expressions/index.md)
