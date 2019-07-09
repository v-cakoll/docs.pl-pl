---
title: Return, instrukcja - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: a845ce257bf7f0cf0e64d6815b2278f6cec946e7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661612"
---
# <a name="return-c-reference"></a><span data-ttu-id="1d471-102">return (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1d471-102">return (C# Reference)</span></span>

<span data-ttu-id="1d471-103">`return` Kończy wykonywanie metody, w którym występuje i zwraca kontrolę do metody wywołującej.</span><span class="sxs-lookup"><span data-stu-id="1d471-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="1d471-104">Może również zwracać wartość opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1d471-104">It can also return an optional value.</span></span> <span data-ttu-id="1d471-105">Jeśli metoda jest `void` typu `return` instrukcji, można pominąć.</span><span class="sxs-lookup"><span data-stu-id="1d471-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="1d471-106">Jeśli znajduje się wewnątrz instrukcji return `try` bloku `finally` bloku, jeśli taki istnieje, zostanie wykonana zanim sterowanie powraca do wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="1d471-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="1d471-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d471-107">Example</span></span>

 <span data-ttu-id="1d471-108">W poniższym przykładzie metoda `CalculateArea()` zwraca zmienna lokalna `area` jako `double` wartość.</span><span class="sxs-lookup"><span data-stu-id="1d471-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="1d471-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1d471-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1d471-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d471-110">See also</span></span>

- [<span data-ttu-id="1d471-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1d471-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1d471-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1d471-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1d471-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="1d471-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1d471-114">return, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1d471-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
