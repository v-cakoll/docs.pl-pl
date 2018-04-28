---
title: do — Powiązania (F#)
description: 'Dowiedz się, jak F # "do" powiązanie służy do wykonywania kodu bez definiowania funkcji lub wartości.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4c63da0c5e2f4130d59f9efa6bc54a55e5fe9fd8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="do-bindings"></a><span data-ttu-id="3bc46-103">do — Powiązania</span><span class="sxs-lookup"><span data-stu-id="3bc46-103">do Bindings</span></span>

<span data-ttu-id="3bc46-104">A `do` powiązanie jest używane do wykonywania kodu bez definiowania funkcji lub wartości.</span><span class="sxs-lookup"><span data-stu-id="3bc46-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="3bc46-105">Również, czy powiązania może być używany w klasach, zobacz [ `do` powiązania w klasach](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="3bc46-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="3bc46-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="3bc46-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="3bc46-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3bc46-107">Remarks</span></span>
<span data-ttu-id="3bc46-108">Użyj `do` powiązanie umożliwia wykonanie kodu niezależnie od definicji funkcji lub wartości.</span><span class="sxs-lookup"><span data-stu-id="3bc46-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="3bc46-109">Wyrażenie w `do` powiązania musi zwracać `unit`.</span><span class="sxs-lookup"><span data-stu-id="3bc46-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="3bc46-110">Kod w najwyższego poziomu `do` powiązania jest wykonywany podczas inicjowania modułu.</span><span class="sxs-lookup"><span data-stu-id="3bc46-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="3bc46-111">Słowo kluczowe `do` jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="3bc46-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="3bc46-112">Atrybuty można zastosować do najwyższego poziomu `do` powiązania.</span><span class="sxs-lookup"><span data-stu-id="3bc46-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="3bc46-113">Na przykład, jeśli jest używana usługa międzyoperacyjna modelu COM, można zastosować `STAThread` atrybutu do programu.</span><span class="sxs-lookup"><span data-stu-id="3bc46-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="3bc46-114">Można to zrobić przy użyciu atrybutu na `do` powiązanie, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="3bc46-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a><span data-ttu-id="3bc46-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bc46-115">See Also</span></span>
[<span data-ttu-id="3bc46-116">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="3bc46-116">F# Language Reference</span></span>](../index.md)

[<span data-ttu-id="3bc46-117">Funkcje</span><span class="sxs-lookup"><span data-stu-id="3bc46-117">Functions</span></span>](index.md)

