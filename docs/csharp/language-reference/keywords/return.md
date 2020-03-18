---
title: instrukcja return - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 116bad7a1f9f61311d287c575b52547d63c9e1c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713134"
---
# <a name="return-c-reference"></a><span data-ttu-id="3fd1d-102">return (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3fd1d-102">return (C# Reference)</span></span>

<span data-ttu-id="3fd1d-103">Instrukcja `return` kończy wykonywanie metody, w którym pojawia się i zwraca kontrolę do metody wywołującej.</span><span class="sxs-lookup"><span data-stu-id="3fd1d-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="3fd1d-104">Można również zwrócić wartość opcjonalną.</span><span class="sxs-lookup"><span data-stu-id="3fd1d-104">It can also return an optional value.</span></span> <span data-ttu-id="3fd1d-105">Jeśli metoda jest `void` typem, instrukcja `return` może zostać pominięta.</span><span class="sxs-lookup"><span data-stu-id="3fd1d-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="3fd1d-106">Jeśli return instrukcji znajduje `try` się `finally` wewnątrz bloku, blok, jeśli istnieje, zostaną wykonane przed kontroli zwraca do metody wywołującej.</span><span class="sxs-lookup"><span data-stu-id="3fd1d-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="3fd1d-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fd1d-107">Example</span></span>

 <span data-ttu-id="3fd1d-108">W poniższym przykładzie `CalculateArea()` metoda zwraca `area` zmienną `double` lokalną jako wartość.</span><span class="sxs-lookup"><span data-stu-id="3fd1d-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="3fd1d-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3fd1d-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3fd1d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3fd1d-110">See also</span></span>

- [<span data-ttu-id="3fd1d-111">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="3fd1d-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3fd1d-112">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="3fd1d-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3fd1d-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="3fd1d-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3fd1d-114">return, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3fd1d-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
