---
title: 'Pętle: while...do — Wyrażenie'
description: Zobacz, jak while... wyrażenie do wykonuje wykonywanie iteracji (zapętlenie), gdy określony warunek testu ma wartość true.
ms.date: 05/16/2016
ms.openlocfilehash: f05bdd9f8f4b9446d59f68e1231fb75e18e9b526
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630751"
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="083a3-103">Pętle: while...do — Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="083a3-103">Loops: while...do Expression</span></span>

<span data-ttu-id="083a3-104">`while...do` Wyrażenie służy do wykonywania iteracji (zapętlanie), gdy określony warunek testu ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="083a3-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>

## <a name="syntax"></a><span data-ttu-id="083a3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="083a3-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="083a3-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="083a3-106">Remarks</span></span>

<span data-ttu-id="083a3-107">*Wyrażenie testowe* jest oceniane; Jeśli tak jest `true`, *wyrażenie treści* jest wykonywane, a wyrażenie testowe jest ponownie oceniane.</span><span class="sxs-lookup"><span data-stu-id="083a3-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="083a3-108">*Wyrażenie treści* musi mieć typ `unit`.</span><span class="sxs-lookup"><span data-stu-id="083a3-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="083a3-109">Jeśli wyrażenie testowe ma wartość `false`, iteracja zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="083a3-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="083a3-110">Poniższy przykład ilustruje użycie `while...do` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="083a3-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="083a3-111">Dane wyjściowe powyższego kodu to strumień liczb losowych z zakresu od 1 do 20, ostatni z 10.</span><span class="sxs-lookup"><span data-stu-id="083a3-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> <span data-ttu-id="083a3-112">Można używać `while...do` w wyrażeniach sekwencji i innych wyrażeniach obliczeniowych, w tym przypadku używana jest dostosowana wersja `while...do` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="083a3-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="083a3-113">Aby uzyskać więcej informacji, [](sequences.md)Zobacz sekwencje, [asynchroniczne przepływy pracy](asynchronous-workflows.md)i [wyrażenia obliczeń](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="083a3-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="083a3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="083a3-114">See also</span></span>

- [<span data-ttu-id="083a3-115">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="083a3-115">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="083a3-116">Pętli `for...in`Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="083a3-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="083a3-117">Pętli `for...to`Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="083a3-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
