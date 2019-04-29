---
title: do — C# odwołania
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 4bdbd1c8efac0b7ba95d4c8d16dae3101fe6bcb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661792"
---
# <a name="do-c-reference"></a><span data-ttu-id="ce3ea-102">do (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ce3ea-102">do (C# Reference)</span></span>

<span data-ttu-id="ce3ea-103">`do` Instrukcji wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne, które daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="ce3ea-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="ce3ea-104">Ponieważ to wyrażenie jest oceniane po każdym wykonaniu pętli, `do-while` pętla jest wykonywana raz lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="ce3ea-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="ce3ea-105">To różni się od [podczas](while.md) pętli, która wykonuje zero lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="ce3ea-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="ce3ea-106">W dowolnym punkcie w `do` blok instrukcji, można zerwać pętlę za pomocą [podziału](break.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ce3ea-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="ce3ea-107">Użytkownik może przechodzić bezpośrednio do obliczania `while` wyrażenie, używając [nadal](continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ce3ea-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="ce3ea-108">Jeśli wyrażenie ma `true`, wykonywanie jest kontynuowane po pierwszej instrukcji w pętli.</span><span class="sxs-lookup"><span data-stu-id="ce3ea-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="ce3ea-109">W przeciwnym razie wykonywanie jest kontynuowane po pierwszej instrukcji następującej po pętli.</span><span class="sxs-lookup"><span data-stu-id="ce3ea-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="ce3ea-110">Możesz również wyjść `do-while` pętli przez [przejdź do](goto.md), [zwracają](return.md), lub [throw](throw.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ce3ea-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="ce3ea-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce3ea-111">Example</span></span>

<span data-ttu-id="ce3ea-112">W poniższym przykładzie pokazano użycie `do` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ce3ea-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="ce3ea-113">Wybierz **Uruchom** do uruchamiania kodu przykładu.</span><span class="sxs-lookup"><span data-stu-id="ce3ea-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="ce3ea-114">Po tym można zmodyfikować kod i uruchom go ponownie.</span><span class="sxs-lookup"><span data-stu-id="ce3ea-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="ce3ea-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ce3ea-115">C# language specification</span></span>

<span data-ttu-id="ce3ea-116">Aby uzyskać więcej informacji, zobacz [instrukcji](~/_csharplang/spec/statements.md#the-do-statement) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce3ea-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ce3ea-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce3ea-117">See also</span></span>

- [<span data-ttu-id="ce3ea-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ce3ea-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ce3ea-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ce3ea-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ce3ea-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="ce3ea-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ce3ea-121">Instrukcje iteracji</span><span class="sxs-lookup"><span data-stu-id="ce3ea-121">Iteration Statements</span></span>](iteration-statements.md)
- [<span data-ttu-id="ce3ea-122">while — instrukcja</span><span class="sxs-lookup"><span data-stu-id="ce3ea-122">while statement</span></span>](while.md)
