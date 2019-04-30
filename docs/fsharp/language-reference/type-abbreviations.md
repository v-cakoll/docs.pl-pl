---
title: Skróty typów
description: Dowiedz się więcej o F# wpisz skróty, aby zapewnić bardziej opisową nazwę typu w celu zwiększenia czytelności kodu.
ms.date: 05/16/2016
ms.openlocfilehash: 0deaef789367aad413e5a537bf7164034e1275c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683343"
---
# <a name="type-abbreviations"></a><span data-ttu-id="ed38f-103">Skróty typów</span><span class="sxs-lookup"><span data-stu-id="ed38f-103">Type Abbreviations</span></span>

<span data-ttu-id="ed38f-104">A *— typ skrótu* to alias lub alternatywną nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="ed38f-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="ed38f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed38f-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="ed38f-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed38f-106">Remarks</span></span>

<span data-ttu-id="ed38f-107">Skróty typów można użyć, aby zapewnić bardziej opisową nazwę typu w celu zwiększenia czytelności kodu.</span><span class="sxs-lookup"><span data-stu-id="ed38f-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="ed38f-108">Umożliwia także je utworzyć łatwy w użyciu nazwy typu, który jest w przeciwnym razie kłopotliwe zapisać. Ponadto można użyć skróty typów ułatwiają zmianę typu podstawowego bez zmiany całego kodu, który używa typu.</span><span class="sxs-lookup"><span data-stu-id="ed38f-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="ed38f-109">To jest skrótem typu prostego.</span><span class="sxs-lookup"><span data-stu-id="ed38f-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="ed38f-110">Wartością domyślną jest dostępność skróty typów `public`.</span><span class="sxs-lookup"><span data-stu-id="ed38f-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="ed38f-111">Skróty typów mogą zawierać parametrów ogólnych, tak jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ed38f-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="ed38f-112">W poprzednim kodzie `Transform` jest skrótem typu reprezentujący funkcja, która przyjmuje jeden argument dowolnego typu i który zwraca pojedynczą wartość tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="ed38f-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="ed38f-113">Skróty typów nie są zachowywane w kodzie .NET Framework MSIL.</span><span class="sxs-lookup"><span data-stu-id="ed38f-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="ed38f-114">W związku z tym, kiedy używasz F# zestawu w innym języku .NET Framework, należy użyć podstawowej nazwy typu dla skrótem typu.</span><span class="sxs-lookup"><span data-stu-id="ed38f-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="ed38f-115">Skróty typów można również w jednostkach miary.</span><span class="sxs-lookup"><span data-stu-id="ed38f-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="ed38f-116">Aby uzyskać więcej informacji, zobacz [jednostki miary](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="ed38f-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed38f-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed38f-117">See also</span></span>

- [<span data-ttu-id="ed38f-118">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="ed38f-118">F# Language Reference</span></span>](index.md)