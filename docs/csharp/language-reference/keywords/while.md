---
title: while — C# odwołania
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 2cf58e2edc5685032c2b9e590bc456e3a4e4d79b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633072"
---
# <a name="while-c-reference"></a><span data-ttu-id="8a8dc-102">while (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8a8dc-102">while (C# Reference)</span></span>

<span data-ttu-id="8a8dc-103">`while` Instrukcji wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne, które daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="8a8dc-104">Ponieważ to wyrażenie jest obliczane przed każdym wykonaniu pętli, `while` pętla jest wykonywana zero lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="8a8dc-105">To różni się od [czy](do.md) pętli, która wykonuje jeden lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="8a8dc-106">W dowolnym punkcie w `while` blok instrukcji, można zerwać pętlę za pomocą [podziału](break.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="8a8dc-107">Użytkownik może przechodzić bezpośrednio do obliczania `while` wyrażenie, używając [nadal](continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="8a8dc-108">Jeśli wyrażenie ma `true`, wykonywanie jest kontynuowane po pierwszej instrukcji w pętli.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="8a8dc-109">W przeciwnym razie wykonywanie jest kontynuowane po pierwszej instrukcji następującej po pętli.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="8a8dc-110">Możesz również wyjść `while` pętli przez [przejdź do](goto.md), [zwracają](return.md), lub [throw](throw.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="8a8dc-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a8dc-111">Example</span></span>

<span data-ttu-id="8a8dc-112">W poniższym przykładzie pokazano użycie `while` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="8a8dc-113">Wybierz **Uruchom** do uruchamiania kodu przykładu.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="8a8dc-114">Po tym można zmodyfikować kod i uruchom go ponownie.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="8a8dc-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8a8dc-115">C# language specification</span></span>

<span data-ttu-id="8a8dc-116">Aby uzyskać więcej informacji, zobacz [while, instrukcja](~/_csharplang/spec/statements.md#the-while-statement) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="8a8dc-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8a8dc-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a8dc-117">See also</span></span>

- [<span data-ttu-id="8a8dc-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8a8dc-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8a8dc-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8a8dc-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8a8dc-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="8a8dc-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8a8dc-121">Instrukcje iteracji</span><span class="sxs-lookup"><span data-stu-id="8a8dc-121">Iteration Statements</span></span>](iteration-statements.md)
- [<span data-ttu-id="8a8dc-122">— Instrukcja</span><span class="sxs-lookup"><span data-stu-id="8a8dc-122">do statement</span></span>](do.md)
