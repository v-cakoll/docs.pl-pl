---
title: do — Powiązania (F#)
description: 'Dowiedz się, jak języka F # czy powiązanie jest używana do wykonywania kodu bez definiowania funkcji lub wartość.'
ms.date: 05/16/2016
ms.openlocfilehash: 78dbf8da0fe40b5af566ad98693df1109eede7e4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "45973147"
---
# <a name="do-bindings"></a><span data-ttu-id="d66c5-103">do — Powiązania</span><span class="sxs-lookup"><span data-stu-id="d66c5-103">do Bindings</span></span>

<span data-ttu-id="d66c5-104">A `do` powiązania jest używany do wykonywania kodu bez definiowania funkcji lub wartości.</span><span class="sxs-lookup"><span data-stu-id="d66c5-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="d66c5-105">Ponadto wykonaj powiązań mogą być używane w klasach, zobacz [ `do` powiązania w klasach](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="d66c5-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="d66c5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d66c5-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="d66c5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d66c5-107">Remarks</span></span>

<span data-ttu-id="d66c5-108">Użyj `do` powiązanie wykonać kod, niezależnie od definicji funkcji lub wartości.</span><span class="sxs-lookup"><span data-stu-id="d66c5-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="d66c5-109">Wyrażenie w `do` powiązania musi zwracać `unit`.</span><span class="sxs-lookup"><span data-stu-id="d66c5-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="d66c5-110">Kod w najwyższego poziomu `do` powiązania jest wykonywany, gdy moduł został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="d66c5-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="d66c5-111">Słowo kluczowe `do` jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d66c5-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="d66c5-112">Atrybuty mogą być stosowane do najwyższego poziomu `do` powiązania.</span><span class="sxs-lookup"><span data-stu-id="d66c5-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="d66c5-113">Na przykład, jeśli program używa Usługa międzyoperacyjna modelu COM, warto zastosować `STAThread` atrybutu do programu.</span><span class="sxs-lookup"><span data-stu-id="d66c5-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="d66c5-114">Można to zrobić za pomocą atrybutu na `do` powiązania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d66c5-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="d66c5-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d66c5-115">See also</span></span>

- [<span data-ttu-id="d66c5-116">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="d66c5-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="d66c5-117">Funkcje</span><span class="sxs-lookup"><span data-stu-id="d66c5-117">Functions</span></span>](index.md)
