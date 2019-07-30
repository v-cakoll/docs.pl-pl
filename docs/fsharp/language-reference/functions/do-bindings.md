---
title: do — Powiązania
description: Dowiedz się F# , w jaki sposób wiązanie "do" służy do wykonywania kodu bez definiowania funkcji ani wartości.
ms.date: 05/16/2016
ms.openlocfilehash: f98f523296bfaceeda35d4861eafbfeaa5a60c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630539"
---
# <a name="do-bindings"></a><span data-ttu-id="1a4d3-103">do — Powiązania</span><span class="sxs-lookup"><span data-stu-id="1a4d3-103">do Bindings</span></span>

<span data-ttu-id="1a4d3-104">`do` Powiązanie służy do wykonywania kodu bez definiowania funkcji lub wartości.</span><span class="sxs-lookup"><span data-stu-id="1a4d3-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="1a4d3-105">Ponadto, aby można było używać powiązań w klasach, zobacz [ `do` powiązania w klasach](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="1a4d3-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="1a4d3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a4d3-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="1a4d3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a4d3-107">Remarks</span></span>

<span data-ttu-id="1a4d3-108">Użyj powiązania `do` , gdy chcesz wykonać kod niezależnie od definicji funkcji lub wartości.</span><span class="sxs-lookup"><span data-stu-id="1a4d3-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="1a4d3-109">Wyrażenie w `do` powiązaniu musi zwracać `unit`.</span><span class="sxs-lookup"><span data-stu-id="1a4d3-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="1a4d3-110">Kod w powiązaniu najwyższego poziomu `do` jest wykonywany po zainicjowaniu modułu.</span><span class="sxs-lookup"><span data-stu-id="1a4d3-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="1a4d3-111">Słowo kluczowe `do` jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="1a4d3-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="1a4d3-112">Atrybuty mogą być stosowane do powiązań najwyższego `do` poziomu.</span><span class="sxs-lookup"><span data-stu-id="1a4d3-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="1a4d3-113">Na przykład jeśli program korzysta z międzyoperacyjności modelu COM, możesz chcieć zastosować `STAThread` atrybut do programu.</span><span class="sxs-lookup"><span data-stu-id="1a4d3-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="1a4d3-114">Można to zrobić przy użyciu atrybutu dla `do` powiązania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1a4d3-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="1a4d3-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a4d3-115">See also</span></span>

- [<span data-ttu-id="1a4d3-116">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="1a4d3-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="1a4d3-117">Funkcje</span><span class="sxs-lookup"><span data-stu-id="1a4d3-117">Functions</span></span>](index.md)
