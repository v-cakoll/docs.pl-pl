---
title: do (odwołanie w C#)
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 89c13f5b547c13052e229ff6eb3a39ae5babce41
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44509632"
---
# <a name="do-c-reference"></a><span data-ttu-id="73bfe-102">do (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="73bfe-102">do (C# Reference)</span></span>

<span data-ttu-id="73bfe-103">`do` Instrukcji wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne, które daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="73bfe-103">The `do` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span> <span data-ttu-id="73bfe-104">Ponieważ to wyrażenie jest oceniane po każdym wykonaniu pętli, `do-while` pętla jest wykonywana raz lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="73bfe-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="73bfe-105">To różni się od [podczas](while.md) pętli, która wykonuje zero lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="73bfe-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="73bfe-106">W dowolnym punkcie w `do` blok instrukcji, można zerwać pętlę za pomocą [podziału](break.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="73bfe-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="73bfe-107">Użytkownik może przechodzić bezpośrednio do obliczania `while` wyrażenie, używając [nadal](continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="73bfe-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="73bfe-108">Jeśli wyrażenie ma `true`, wykonywanie jest kontynuowane po pierwszej instrukcji w pętli.</span><span class="sxs-lookup"><span data-stu-id="73bfe-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="73bfe-109">W przeciwnym razie wykonywanie jest kontynuowane po pierwszej instrukcji następującej po pętli.</span><span class="sxs-lookup"><span data-stu-id="73bfe-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="73bfe-110">Możesz również wyjść `do-while` pętli przez [przejdź do](goto.md), [zwracają](return.md), lub [throw](throw.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="73bfe-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="73bfe-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="73bfe-111">Example</span></span>

<span data-ttu-id="73bfe-112">W poniższym przykładzie pokazano użycie `do` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="73bfe-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="73bfe-113">Wybierz **Uruchom** do uruchamiania kodu przykładu.</span><span class="sxs-lookup"><span data-stu-id="73bfe-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="73bfe-114">Po tym można zmodyfikować kod i uruchom go ponownie.</span><span class="sxs-lookup"><span data-stu-id="73bfe-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="73bfe-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="73bfe-115">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="73bfe-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73bfe-116">See also</span></span>

- [<span data-ttu-id="73bfe-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="73bfe-117">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="73bfe-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="73bfe-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="73bfe-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="73bfe-119">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="73bfe-120">do-while, instrukcja (C++)</span><span class="sxs-lookup"><span data-stu-id="73bfe-120">do-while Statement (C++)</span></span>](/cpp/cpp/do-while-statement-cpp)  
- [<span data-ttu-id="73bfe-121">Instrukcje iteracji</span><span class="sxs-lookup"><span data-stu-id="73bfe-121">Iteration Statements</span></span>](iteration-statements.md)  
- [<span data-ttu-id="73bfe-122">while — instrukcja</span><span class="sxs-lookup"><span data-stu-id="73bfe-122">while statement</span></span>](while.md)  
