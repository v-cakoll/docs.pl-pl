---
title: do — Powiązania (F#)
description: 'Dowiedz się, jak języka F # czy powiązanie jest używana do wykonywania kodu bez definiowania funkcji lub wartość.'
ms.date: 05/16/2016
ms.openlocfilehash: 78dbf8da0fe40b5af566ad98693df1109eede7e4
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353099"
---
# <a name="do-bindings"></a><span data-ttu-id="8444d-103">do — Powiązania</span><span class="sxs-lookup"><span data-stu-id="8444d-103">do Bindings</span></span>

<span data-ttu-id="8444d-104">A `do` powiązania jest używany do wykonywania kodu bez definiowania funkcji lub wartości.</span><span class="sxs-lookup"><span data-stu-id="8444d-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="8444d-105">Ponadto wykonaj powiązań mogą być używane w klasach, zobacz [ `do` powiązania w klasach](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="8444d-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="8444d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="8444d-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="8444d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8444d-107">Remarks</span></span>

<span data-ttu-id="8444d-108">Użyj `do` powiązanie wykonać kod, niezależnie od definicji funkcji lub wartości.</span><span class="sxs-lookup"><span data-stu-id="8444d-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="8444d-109">Wyrażenie w `do` powiązania musi zwracać `unit`.</span><span class="sxs-lookup"><span data-stu-id="8444d-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="8444d-110">Kod w najwyższego poziomu `do` powiązania jest wykonywany, gdy moduł został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="8444d-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="8444d-111">Słowo kluczowe `do` jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="8444d-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="8444d-112">Atrybuty mogą być stosowane do najwyższego poziomu `do` powiązania.</span><span class="sxs-lookup"><span data-stu-id="8444d-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="8444d-113">Na przykład, jeśli program używa Usługa międzyoperacyjna modelu COM, warto zastosować `STAThread` atrybutu do programu.</span><span class="sxs-lookup"><span data-stu-id="8444d-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="8444d-114">Można to zrobić za pomocą atrybutu na `do` powiązania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8444d-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="8444d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8444d-115">See also</span></span>

- [<span data-ttu-id="8444d-116">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="8444d-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="8444d-117">Funkcje</span><span class="sxs-lookup"><span data-stu-id="8444d-117">Functions</span></span>](index.md)
