---
title: Return — instrukcja C# -Reference
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 116bad7a1f9f61311d287c575b52547d63c9e1c0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713134"
---
# <a name="return-c-reference"></a><span data-ttu-id="26b1b-102">return (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="26b1b-102">return (C# Reference)</span></span>

<span data-ttu-id="26b1b-103">Instrukcja `return` przerywa wykonywanie metody, w której występuje i zwraca kontrolę do metody wywołującej.</span><span class="sxs-lookup"><span data-stu-id="26b1b-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="26b1b-104">Może również zwrócić wartość opcjonalną.</span><span class="sxs-lookup"><span data-stu-id="26b1b-104">It can also return an optional value.</span></span> <span data-ttu-id="26b1b-105">Jeśli metoda jest typu `void`, instrukcja `return` może zostać pominięta.</span><span class="sxs-lookup"><span data-stu-id="26b1b-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="26b1b-106">Jeśli instrukcja return znajduje się wewnątrz bloku `try`, blok `finally`, jeśli taki istnieje, zostanie wykonany przed powracaniem kontroli do metody wywołującej.</span><span class="sxs-lookup"><span data-stu-id="26b1b-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="26b1b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="26b1b-107">Example</span></span>

 <span data-ttu-id="26b1b-108">W poniższym przykładzie metoda `CalculateArea()` zwraca zmienną lokalną `area` jako wartość `double`.</span><span class="sxs-lookup"><span data-stu-id="26b1b-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="26b1b-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="26b1b-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="26b1b-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26b1b-110">See also</span></span>

- [<span data-ttu-id="26b1b-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="26b1b-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="26b1b-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="26b1b-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="26b1b-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="26b1b-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="26b1b-114">return, instrukcja</span><span class="sxs-lookup"><span data-stu-id="26b1b-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
