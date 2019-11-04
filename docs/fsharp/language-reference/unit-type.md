---
title: Typ jednostki
description: Dowiedz się F# , w jaki sposób typ "Unit" jest często używany do przechowywania wartości wymaganej przez składnię języka, gdy wartość nie jest potrzebna lub nie jest wymagana.
ms.date: 05/16/2016
ms.openlocfilehash: a5960fb05af50486a78345d10a5ad913e65729e3
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424031"
---
# <a name="unit-type"></a><span data-ttu-id="12401-103">Typ jednostki</span><span class="sxs-lookup"><span data-stu-id="12401-103">Unit Type</span></span>

<span data-ttu-id="12401-104">Typ `unit` jest typem, który wskazuje brak określonej wartości; Typ `unit` ma tylko jedną wartość, która działa jako symbol zastępczy, gdy inna wartość nie istnieje lub nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="12401-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>

## <a name="syntax"></a><span data-ttu-id="12401-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="12401-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="12401-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="12401-106">Remarks</span></span>

<span data-ttu-id="12401-107">Każde F# wyrażenie musi być szacowane do wartości.</span><span class="sxs-lookup"><span data-stu-id="12401-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="12401-108">W przypadku wyrażeń, które nie generują wartości będącej przedmiotem zainteresowania, używana jest wartość typu `unit`.</span><span class="sxs-lookup"><span data-stu-id="12401-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="12401-109">Typ `unit` jest podobny do typu `void` w językach takich jak C# i. C++</span><span class="sxs-lookup"><span data-stu-id="12401-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="12401-110">Typ `unit` ma jedną wartość, a ta wartość jest wskazywana przez `()`tokenu.</span><span class="sxs-lookup"><span data-stu-id="12401-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="12401-111">Wartość typu `unit` jest często używana w F# programowaniu do przechowywania miejsca, w którym wartość jest wymagana przez składnię języka, ale gdy wartość nie jest potrzebna lub nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="12401-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="12401-112">Przykład może być wartością zwracaną funkcji `printf`.</span><span class="sxs-lookup"><span data-stu-id="12401-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="12401-113">Ponieważ ważne akcje operacji `printf` są wykonywane w funkcji, funkcja nie musi zwracać wartości rzeczywistej.</span><span class="sxs-lookup"><span data-stu-id="12401-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="12401-114">W związku z tym wartość zwracana jest typu `unit`.</span><span class="sxs-lookup"><span data-stu-id="12401-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="12401-115">Niektóre konstrukcje oczekują wartości `unit`.</span><span class="sxs-lookup"><span data-stu-id="12401-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="12401-116">Na przykład do wartości `unit` należy obliczyć `do` powiązanie lub dowolny kod na najwyższym poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="12401-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="12401-117">Kompilator zgłasza ostrzeżenie, gdy powiązanie `do` lub kod na najwyższym poziomie modułu generuje wynik inny niż wartość `unit`, która nie jest używana, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="12401-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="12401-118">To ostrzeżenie jest cechą programowania funkcjonalnego; nie jest ona wyświetlana w innych językach programowania .NET.</span><span class="sxs-lookup"><span data-stu-id="12401-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="12401-119">W czystym programie funkcjonalnym, w którym funkcje nie mają żadnych efektów ubocznych, końcowa wartość zwracana jest jedynym wynikiem wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="12401-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="12401-120">W związku z tym, gdy wynik jest ignorowany, jest to możliwy błąd programowania.</span><span class="sxs-lookup"><span data-stu-id="12401-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="12401-121">Chociaż F# nie jest to czysto funkcjonalny język programowania, dobrym sposobem jest przestrzeganie stylu programowania funkcjonalnego, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="12401-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="12401-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12401-122">See also</span></span>

- [<span data-ttu-id="12401-123">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="12401-123">Primitive</span></span>](basic-types.md)
- [<span data-ttu-id="12401-124">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="12401-124">F# Language Reference</span></span>](index.md)
