---
title: Skróty typów (F#)
description: 'Więcej informacji na temat skróty typów F # umożliwiają typu bardziej zrozumiałej nazwy w celu ułatwienia kodu.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: bf17ee9795947fdc11fe958f09d52f5730b95bf8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="type-abbreviations"></a><span data-ttu-id="494d2-103">Skróty typów</span><span class="sxs-lookup"><span data-stu-id="494d2-103">Type Abbreviations</span></span>

<span data-ttu-id="494d2-104">A *— skrót typu* jest alias lub alternatywną nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="494d2-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="494d2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="494d2-105">Syntax</span></span>

```fsharp
type type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="494d2-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="494d2-106">Remarks</span></span>
<span data-ttu-id="494d2-107">Skróty typów umożliwia zapewniają bardziej zrozumiałej nazwy, aby poprawić czytelność kodu typu.</span><span class="sxs-lookup"><span data-stu-id="494d2-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="494d2-108">Ponadto można użyć do utworzenia łatwy w użyciu nazwy typu, który jest skomplikowane, aby zapisać. Ponadto można użyć skróty typów ułatwiające zmienić typu podstawowego bez zmieniania kodu, który używa typu.</span><span class="sxs-lookup"><span data-stu-id="494d2-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="494d2-109">Poniżej znajduje się skrót typu prostego.</span><span class="sxs-lookup"><span data-stu-id="494d2-109">The following is a simple type abbreviation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="494d2-110">Skróty typów mogą zawierać parametrów ogólnych, zgodnie z poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="494d2-110">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="494d2-111">W poprzednim kodzie `Transform` jest skrót typu, który reprezentuje funkcję, która pobiera jeden argument typu i która zwraca pojedynczą wartość tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="494d2-111">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="494d2-112">Skróty typów nie są zachowywane w kodzie programu .NET Framework MSIL.</span><span class="sxs-lookup"><span data-stu-id="494d2-112">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="494d2-113">W związku z tym gdy używasz zestawu F # z innego języka .NET Framework, należy użyć podstawowej nazwy typu dla skrót typu.</span><span class="sxs-lookup"><span data-stu-id="494d2-113">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="494d2-114">Skróty typów można również na jednostki miary.</span><span class="sxs-lookup"><span data-stu-id="494d2-114">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="494d2-115">Aby uzyskać więcej informacji, zobacz [jednostki miary](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="494d2-115">For more information, see [Units of Measure](units-of-measure.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="494d2-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="494d2-116">See Also</span></span>
[<span data-ttu-id="494d2-117">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="494d2-117">F# Language Reference</span></span>](index.md)

