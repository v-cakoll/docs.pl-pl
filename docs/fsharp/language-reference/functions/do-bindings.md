---
title: "do — Powiązania (F#)"
description: "Dowiedz się, jak F # \"do\" powiązanie służy do wykonywania kodu bez definiowania funkcji lub wartości."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4c1057a3-3aa1-4b64-b46a-25ffe33f0be9
ms.openlocfilehash: f2563d384b67c005c96c2ff487c786476d385e70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="do-bindings"></a><span data-ttu-id="67ebe-104">do — Powiązania</span><span class="sxs-lookup"><span data-stu-id="67ebe-104">do Bindings</span></span>

<span data-ttu-id="67ebe-105">A `do` powiązanie jest używane do wykonywania kodu bez definiowania funkcji lub wartości.</span><span class="sxs-lookup"><span data-stu-id="67ebe-105">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="67ebe-106">Również, czy powiązania może być używany w klasach, zobacz [ `do` powiązania w klasach](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="67ebe-106">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="67ebe-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="67ebe-107">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="67ebe-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67ebe-108">Remarks</span></span>
<span data-ttu-id="67ebe-109">Użyj `do` powiązanie umożliwia wykonanie kodu niezależnie od definicji funkcji lub wartości.</span><span class="sxs-lookup"><span data-stu-id="67ebe-109">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="67ebe-110">Wyrażenie w `do` powiązania musi zwracać `unit`.</span><span class="sxs-lookup"><span data-stu-id="67ebe-110">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="67ebe-111">Kod w najwyższego poziomu `do` powiązania jest wykonywany podczas inicjowania modułu.</span><span class="sxs-lookup"><span data-stu-id="67ebe-111">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="67ebe-112">Słowo kluczowe `do` jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="67ebe-112">The keyword `do` is optional.</span></span>

<span data-ttu-id="67ebe-113">Atrybuty można zastosować do najwyższego poziomu `do` powiązania.</span><span class="sxs-lookup"><span data-stu-id="67ebe-113">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="67ebe-114">Na przykład, jeśli jest używana usługa międzyoperacyjna modelu COM, można zastosować `STAThread` atrybutu do programu.</span><span class="sxs-lookup"><span data-stu-id="67ebe-114">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="67ebe-115">Można to zrobić przy użyciu atrybutu na `do` powiązanie, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="67ebe-115">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a><span data-ttu-id="67ebe-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67ebe-116">See Also</span></span>
[<span data-ttu-id="67ebe-117">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="67ebe-117">F# Language Reference</span></span>](../index.md)

[<span data-ttu-id="67ebe-118">Funkcje</span><span class="sxs-lookup"><span data-stu-id="67ebe-118">Functions</span></span>](index.md)

