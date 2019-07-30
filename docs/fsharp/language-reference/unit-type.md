---
title: Typ jednostki
description: Dowiedz się F# , w jaki sposób typ "Unit" jest często używany do przechowywania wartości wymaganej przez składnię języka, gdy wartość nie jest potrzebna lub nie jest wymagana.
ms.date: 05/16/2016
ms.openlocfilehash: 4e586702324565b8dcd4f6c7e11a0e1754f89c58
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630177"
---
# <a name="unit-type"></a><span data-ttu-id="7987d-103">Typ jednostki</span><span class="sxs-lookup"><span data-stu-id="7987d-103">Unit Type</span></span>

<span data-ttu-id="7987d-104">Typ jest typem, który wskazuje brak określonej wartości `unit` ; typ ma tylko jedną wartość, która działa jako symbol zastępczy, gdy inna wartość nie istnieje lub nie jest wymagana. `unit`</span><span class="sxs-lookup"><span data-stu-id="7987d-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>

## <a name="syntax"></a><span data-ttu-id="7987d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7987d-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="7987d-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7987d-106">Remarks</span></span>

<span data-ttu-id="7987d-107">Każde F# wyrażenie musi być szacowane do wartości.</span><span class="sxs-lookup"><span data-stu-id="7987d-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="7987d-108">W przypadku wyrażeń, które nie generują wartości będącej przedmiotem zainteresowania, używana jest wartość `unit` typu.</span><span class="sxs-lookup"><span data-stu-id="7987d-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="7987d-109">Typ `unit` jest podobny do `void` typu w językach, takich jak C# i C++.</span><span class="sxs-lookup"><span data-stu-id="7987d-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="7987d-110">Typ ma pojedynczą wartość, a ta wartość jest wskazywana przez token `()`. `unit`</span><span class="sxs-lookup"><span data-stu-id="7987d-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="7987d-111">Wartość `unit` typu jest często używana w F# programowaniu do przechowywania miejsca, w którym wartość jest wymagana przez składnię języka, ale gdy wartość nie jest potrzebna lub nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="7987d-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="7987d-112">Przykładem może być wartość `printf` zwracana przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="7987d-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="7987d-113">Ponieważ ważne akcje `printf` operacji są wykonywane w funkcji, funkcja nie musi zwracać wartości rzeczywistej.</span><span class="sxs-lookup"><span data-stu-id="7987d-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="7987d-114">W związku z tym wartość zwracana jest typu `unit`.</span><span class="sxs-lookup"><span data-stu-id="7987d-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="7987d-115">Niektóre konstrukcje oczekują `unit` wartości.</span><span class="sxs-lookup"><span data-stu-id="7987d-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="7987d-116">Na przykład, `do` oczekiwane jest powiązanie lub dowolny kod na najwyższym poziomie modułu, który ma zostać obliczony `unit` do wartości.</span><span class="sxs-lookup"><span data-stu-id="7987d-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="7987d-117">Kompilator zgłasza ostrzeżenie, gdy `do` powiązanie lub kod na najwyższym poziomie modułu generuje wynik inny `unit` niż wartość, która nie jest używana, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7987d-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="7987d-118">To ostrzeżenie jest cechą programowania funkcjonalnego; nie jest ona wyświetlana w innych językach programowania .NET.</span><span class="sxs-lookup"><span data-stu-id="7987d-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="7987d-119">W czystym programie funkcjonalnym, w którym funkcje nie mają żadnych efektów ubocznych, końcowa wartość zwracana jest jedynym wynikiem wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="7987d-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="7987d-120">W związku z tym, gdy wynik jest ignorowany, jest to możliwy błąd programowania.</span><span class="sxs-lookup"><span data-stu-id="7987d-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="7987d-121">Chociaż F# nie jest to czysto funkcjonalny język programowania, dobrym sposobem jest przestrzeganie stylu programowania funkcjonalnego, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="7987d-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="7987d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7987d-122">See also</span></span>

- [<span data-ttu-id="7987d-123">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="7987d-123">Primitive</span></span>](primitive-types.md)
- [<span data-ttu-id="7987d-124">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="7987d-124">F# Language Reference</span></span>](index.md)
