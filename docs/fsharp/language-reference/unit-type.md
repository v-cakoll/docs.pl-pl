---
title: Typ jednostki (F#)
description: 'Dowiedz się, jak typu "unit" F # jest często używane do przechowywania w miejscu, gdzie wartość jest wymagana przez składni języka żadnej wartości jest wymagane lub pożądane.'
ms.date: 05/16/2016
ms.openlocfilehash: fdd6b62f9d5c6d73407d5326c7d1f66d55780682
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564423"
---
# <a name="unit-type"></a><span data-ttu-id="9ee08-103">Typ jednostki</span><span class="sxs-lookup"><span data-stu-id="9ee08-103">Unit Type</span></span>

<span data-ttu-id="9ee08-104">`unit` Typ jest typem, który wskazuje brak określonej wartości; `unit` typ ma tylko jedną wartość, który działa jako symbol zastępczy, gdy żadna inna wartość istnieje lub jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="9ee08-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>


## <a name="syntax"></a><span data-ttu-id="9ee08-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ee08-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="9ee08-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ee08-106">Remarks</span></span>
<span data-ttu-id="9ee08-107">Każdy F # wyrażenia musi być wartością.</span><span class="sxs-lookup"><span data-stu-id="9ee08-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="9ee08-108">Dla wyrażeń, które nie generują wartość, która ma znaczenie, wartość typu `unit` jest używany.</span><span class="sxs-lookup"><span data-stu-id="9ee08-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="9ee08-109">`unit` Podobny typ `void` typu w językach takich jak C# i C++.</span><span class="sxs-lookup"><span data-stu-id="9ee08-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="9ee08-110">`unit` Pojedynczą wartość ma typ, a ta wartość jest wskazywana przez token `()`.</span><span class="sxs-lookup"><span data-stu-id="9ee08-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="9ee08-111">Wartość `unit` typ jest często używany w języku F # programowania do przechowywania miejsce w przypadku, gdy wartość jest wymagana przez składni języka, ale w przypadku, gdy żadna wartość jest wymagane lub pożądane.</span><span class="sxs-lookup"><span data-stu-id="9ee08-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="9ee08-112">Przykładem może być zwracana wartość `printf` funkcji.</span><span class="sxs-lookup"><span data-stu-id="9ee08-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="9ee08-113">Ponieważ ważne działania `printf` wykonać operacji w funkcji funkcji nie musi zwracać wartość rzeczywistą.</span><span class="sxs-lookup"><span data-stu-id="9ee08-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="9ee08-114">W związku z tym jest zwracana wartość typu `unit`.</span><span class="sxs-lookup"><span data-stu-id="9ee08-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="9ee08-115">Niektóre konstrukcje oczekiwać `unit` wartość.</span><span class="sxs-lookup"><span data-stu-id="9ee08-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="9ee08-116">Na przykład `do` binding lub dowolny kod na najwyższym poziomie modułu powinien zwrócić `unit` wartość.</span><span class="sxs-lookup"><span data-stu-id="9ee08-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="9ee08-117">Kompilator zgłosi ostrzeżenie podczas `do` powiązanie lub kod na najwyższym poziomie modułu powstaje innych niż `unit` wartość, która nie jest używany, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9ee08-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="9ee08-118">To ostrzeżenie jest to cecha programowanie funkcjonalne; nie ma w innych .NET języków programowania.</span><span class="sxs-lookup"><span data-stu-id="9ee08-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="9ee08-119">W programie czysto funkcjonalności, funkcje nie są wszystkie efekty uboczne końcowej zwracany jest jedynym wynikiem wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="9ee08-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="9ee08-120">W związku z tym gdy wynik jest ignorowane, jest możliwy błąd programowania.</span><span class="sxs-lookup"><span data-stu-id="9ee08-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="9ee08-121">Chociaż F # nie jest całkowicie funkcjonalny język programowania, jest dobrą praktyką jest wykonaj funkcjonalności styl programowania, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="9ee08-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ee08-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ee08-122">See Also</span></span>
[<span data-ttu-id="9ee08-123">Pierwotne</span><span class="sxs-lookup"><span data-stu-id="9ee08-123">Primitive</span></span>](primitive-types.md)

[<span data-ttu-id="9ee08-124">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="9ee08-124">F# Language Reference</span></span>](index.md)
