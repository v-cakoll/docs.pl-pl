---
title: Typ jednostki (F#)
description: "Dowiedz się, jak typu \"unit\" F # jest często używane do przechowywania w miejscu, gdzie wartość jest wymagana przez składni języka żadnej wartości jest wymagane lub pożądane."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: eabbb6d7-80f3-4fa5-80b4-0f48982466a7
ms.openlocfilehash: 60ac08c0e3f8380a8f9dec7a083ede93c68bb0e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="unit-type"></a><span data-ttu-id="13c6d-104">Typ jednostki</span><span class="sxs-lookup"><span data-stu-id="13c6d-104">Unit Type</span></span>

<span data-ttu-id="13c6d-105">`unit` Typ jest typem, który wskazuje brak określonej wartości; `unit` typ ma tylko jedną wartość, który działa jako symbol zastępczy, gdy żadna inna wartość istnieje lub jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="13c6d-105">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>


## <a name="syntax"></a><span data-ttu-id="13c6d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="13c6d-106">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="13c6d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13c6d-107">Remarks</span></span>
<span data-ttu-id="13c6d-108">Każdy F # wyrażenia musi być wartością.</span><span class="sxs-lookup"><span data-stu-id="13c6d-108">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="13c6d-109">Dla wyrażeń, które nie generują wartość, która ma znaczenie, wartość typu `unit` jest używany.</span><span class="sxs-lookup"><span data-stu-id="13c6d-109">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="13c6d-110">`unit` Podobny typ `void` typu w językach takich jak C# i C++.</span><span class="sxs-lookup"><span data-stu-id="13c6d-110">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="13c6d-111">`unit` Pojedynczą wartość ma typ, a ta wartość jest wskazywana przez token `()`.</span><span class="sxs-lookup"><span data-stu-id="13c6d-111">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="13c6d-112">Wartość `unit` typ jest często używany w języku F # programowania do przechowywania miejsce w przypadku, gdy wartość jest wymagana przez składni języka, ale w przypadku, gdy żadna wartość jest wymagane lub pożądane.</span><span class="sxs-lookup"><span data-stu-id="13c6d-112">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="13c6d-113">Przykładem może być zwracana wartość `printf` funkcji.</span><span class="sxs-lookup"><span data-stu-id="13c6d-113">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="13c6d-114">Ponieważ ważne działania `printf` wykonać operacji w funkcji funkcji nie musi zwracać wartość rzeczywistą.</span><span class="sxs-lookup"><span data-stu-id="13c6d-114">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="13c6d-115">W związku z tym jest zwracana wartość typu `unit`.</span><span class="sxs-lookup"><span data-stu-id="13c6d-115">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="13c6d-116">Niektóre konstrukcje oczekiwać `unit` wartość.</span><span class="sxs-lookup"><span data-stu-id="13c6d-116">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="13c6d-117">Na przykład `do` binding lub dowolny kod na najwyższym poziomie modułu powinien zwrócić `unit` wartość.</span><span class="sxs-lookup"><span data-stu-id="13c6d-117">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="13c6d-118">Kompilator zgłosi ostrzeżenie podczas `do` powiązanie lub kod na najwyższym poziomie modułu powstaje innych niż `unit` wartość, która nie jest używany, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="13c6d-118">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="13c6d-119">To ostrzeżenie jest to cecha programowanie funkcjonalne; nie ma w innych .NET języków programowania.</span><span class="sxs-lookup"><span data-stu-id="13c6d-119">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="13c6d-120">W programie czysto funkcjonalności, funkcje nie są wszystkie efekty uboczne końcowej zwracany jest jedynym wynikiem wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="13c6d-120">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="13c6d-121">W związku z tym gdy wynik jest ignorowane, jest możliwy błąd programowania.</span><span class="sxs-lookup"><span data-stu-id="13c6d-121">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="13c6d-122">Chociaż F # nie jest całkowicie funkcjonalny język programowania, jest dobrą praktyką jest wykonaj funkcjonalności styl programowania, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="13c6d-122">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="13c6d-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13c6d-123">See Also</span></span>
[<span data-ttu-id="13c6d-124">Pierwotne</span><span class="sxs-lookup"><span data-stu-id="13c6d-124">Primitive</span></span>](primitive-types.md)

[<span data-ttu-id="13c6d-125">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="13c6d-125">F# Language Reference</span></span>](index.md)
