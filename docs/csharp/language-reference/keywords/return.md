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
ms.openlocfilehash: 058dc1d51099196559bee4ec2b96dc883e813f93
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236561"
---
# <a name="return-c-reference"></a><span data-ttu-id="daea8-102">return (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="daea8-102">return (C# Reference)</span></span>

<span data-ttu-id="daea8-103">`return` Kończy wykonywanie metody, w którym występuje i zwraca kontrolę do metody wywołującej.</span><span class="sxs-lookup"><span data-stu-id="daea8-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="daea8-104">Może również zwracać wartość opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="daea8-104">It can also return an optional value.</span></span> <span data-ttu-id="daea8-105">Jeśli metoda jest `void` typu `return` instrukcji, można pominąć.</span><span class="sxs-lookup"><span data-stu-id="daea8-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="daea8-106">Jeśli znajduje się wewnątrz instrukcji return `try` bloku `finally` bloku, jeśli taki istnieje, zostanie wykonana zanim sterowanie powraca do wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="daea8-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="daea8-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="daea8-107">Example</span></span>

 <span data-ttu-id="daea8-108">W poniższym przykładzie metoda `CalculateArea()` zwraca zmienna lokalna `area` jako [double](double.md) wartość.</span><span class="sxs-lookup"><span data-stu-id="daea8-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a [double](double.md) value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="daea8-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="daea8-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="daea8-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="daea8-110">See also</span></span>

- [<span data-ttu-id="daea8-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="daea8-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="daea8-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="daea8-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="daea8-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="daea8-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="daea8-114">return, instrukcja</span><span class="sxs-lookup"><span data-stu-id="daea8-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
- [<span data-ttu-id="daea8-115">Instrukcje skoku</span><span class="sxs-lookup"><span data-stu-id="daea8-115">Jump Statements</span></span>](jump-statements.md)
