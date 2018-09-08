---
title: Skróty typów (F#)
description: 'Więcej informacji na temat typu skróty F #, aby zapewnić bardziej opisową nazwę typu w celu zwiększenia czytelności kodu.'
ms.date: 05/16/2016
ms.openlocfilehash: 259cd6c84e22fc7c98e08255d3e0ded5b87af352
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44176773"
---
# <a name="type-abbreviations"></a><span data-ttu-id="1c096-103">Skróty typów</span><span class="sxs-lookup"><span data-stu-id="1c096-103">Type Abbreviations</span></span>

<span data-ttu-id="1c096-104">A *— typ skrótu* to alias lub alternatywną nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="1c096-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="1c096-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c096-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="1c096-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c096-106">Remarks</span></span>

<span data-ttu-id="1c096-107">Skróty typów można użyć, aby zapewnić bardziej opisową nazwę typu w celu zwiększenia czytelności kodu.</span><span class="sxs-lookup"><span data-stu-id="1c096-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="1c096-108">Umożliwia także je utworzyć łatwy w użyciu nazwy typu, który jest w przeciwnym razie kłopotliwe zapisać. Ponadto można użyć skróty typów ułatwiają zmianę typu podstawowego bez zmiany całego kodu, który używa typu.</span><span class="sxs-lookup"><span data-stu-id="1c096-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="1c096-109">To jest skrótem typu prostego.</span><span class="sxs-lookup"><span data-stu-id="1c096-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="1c096-110">Wartością domyślną jest dostępność skróty typów `public`.</span><span class="sxs-lookup"><span data-stu-id="1c096-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="1c096-111">Skróty typów mogą zawierać parametrów ogólnych, tak jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1c096-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="1c096-112">W poprzednim kodzie `Transform` jest skrótem typu reprezentujący funkcja, która przyjmuje jeden argument dowolnego typu i który zwraca pojedynczą wartość tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="1c096-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="1c096-113">Skróty typów nie są zachowywane w kodzie .NET Framework MSIL.</span><span class="sxs-lookup"><span data-stu-id="1c096-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="1c096-114">W związku z tym gdy używasz zestawu F # w innym języku .NET Framework, należy użyć podstawowej nazwę typu skrótem typu.</span><span class="sxs-lookup"><span data-stu-id="1c096-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="1c096-115">Skróty typów można również w jednostkach miary.</span><span class="sxs-lookup"><span data-stu-id="1c096-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="1c096-116">Aby uzyskać więcej informacji, zobacz [jednostki miary](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="1c096-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c096-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c096-117">See also</span></span>

- [<span data-ttu-id="1c096-118">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="1c096-118">F# Language Reference</span></span>](index.md)
