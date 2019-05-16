---
title: Typ jednostki
description: Dowiedz się, jak F# typ "jednostka" jest często używany do przechowywania to miejsce, w której wartość jest wymagana przez składnię języka żadnej wartości jest wymagane lub pożądane.
ms.date: 05/16/2016
ms.openlocfilehash: d515e19489bfa7de6f17194fd74176cfa0bcd7c9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645122"
---
# <a name="unit-type"></a><span data-ttu-id="b8389-103">Typ jednostki</span><span class="sxs-lookup"><span data-stu-id="b8389-103">Unit Type</span></span>

<span data-ttu-id="b8389-104">`unit` Typ to typ, który wskazuje brak określonej wartości; `unit` typ ma tylko jedną wartość, która działa jako symbolu zastępczego, gdy żadna inna wartość istnieje lub jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="b8389-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8389-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8389-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="b8389-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8389-106">Remarks</span></span>

<span data-ttu-id="b8389-107">Każdy F# wyrażenia musi być wartością.</span><span class="sxs-lookup"><span data-stu-id="b8389-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="b8389-108">W wyrażeniach, które nie generują wartość, która ma znaczenie, wartości typu `unit` jest używany.</span><span class="sxs-lookup"><span data-stu-id="b8389-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="b8389-109">`unit` Przypomina typu `void` typu w językach takich jak C# i C++.</span><span class="sxs-lookup"><span data-stu-id="b8389-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="b8389-110">`unit` Typ ma pojedynczą wartość, a ta wartość jest wskazywany przez token `()`.</span><span class="sxs-lookup"><span data-stu-id="b8389-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="b8389-111">Wartość `unit` typ jest często używany w F# programowania do przechowywania to miejsce, w przypadku, gdy wartość jest wymagana przez składnię języka, ale w przypadku, gdy wartość nie jest wymagane lub żądane.</span><span class="sxs-lookup"><span data-stu-id="b8389-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="b8389-112">Przykładem może być wartość zwracaną przez `printf` funkcji.</span><span class="sxs-lookup"><span data-stu-id="b8389-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="b8389-113">Ponieważ ważne akcje `printf` wykonać operacji w funkcji funkcji nie musi zwracać wartość rzeczywistą.</span><span class="sxs-lookup"><span data-stu-id="b8389-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="b8389-114">W związku z tym, zwracana wartość jest typu `unit`.</span><span class="sxs-lookup"><span data-stu-id="b8389-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="b8389-115">Oczekiwać pewnych konstrukcji `unit` wartość.</span><span class="sxs-lookup"><span data-stu-id="b8389-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="b8389-116">Na przykład `do` powiązania lub dowolnego kodu na najwyższym poziomie modułu powinien zwrócić `unit` wartość.</span><span class="sxs-lookup"><span data-stu-id="b8389-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="b8389-117">Kompilator zgłosi ostrzeżenie podczas `do` powiązaniem lub kodem na najwyższym poziomie modułu daje wynik innych niż `unit` wartość, która nie jest używany, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b8389-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="b8389-118">To ostrzeżenie jest to cecha programowania funkcjonalnego. nie ma w innych .NET, języków programowania.</span><span class="sxs-lookup"><span data-stu-id="b8389-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="b8389-119">W programie czysto funkcjonalności, funkcje nie są wszelkie efekty uboczne końcowa wartość zwracana jest tylko wynik wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="b8389-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="b8389-120">W związku z tym gdy wynik jest ignorowane, jest możliwy błąd programowania.</span><span class="sxs-lookup"><span data-stu-id="b8389-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="b8389-121">Mimo że F# nie jest całkowicie funkcjonalny język programowania, jest dobrym rozwiązaniem, postępuj zgodnie z funkcjonalności stylu programowania, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="b8389-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8389-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8389-122">See also</span></span>

- [<span data-ttu-id="b8389-123">Pierwotny</span><span class="sxs-lookup"><span data-stu-id="b8389-123">Primitive</span></span>](primitive-types.md)
- [<span data-ttu-id="b8389-124">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="b8389-124">F# Language Reference</span></span>](index.md)
