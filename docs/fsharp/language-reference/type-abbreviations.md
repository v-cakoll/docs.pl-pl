---
title: "Skróty typów (F#)"
description: "Więcej informacji na temat skróty typów F # umożliwiają typu bardziej zrozumiałej nazwy w celu ułatwienia kodu."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 560af74f-935f-415c-af56-604cddb9da6b
ms.openlocfilehash: 235c0240fe89d203b9474dec2b3f91947f453cd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="type-abbreviations"></a><span data-ttu-id="198f1-104">Skróty typów</span><span class="sxs-lookup"><span data-stu-id="198f1-104">Type Abbreviations</span></span>

<span data-ttu-id="198f1-105">A *— skrót typu* jest alias lub alternatywną nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="198f1-105">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="198f1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="198f1-106">Syntax</span></span>

```fsharp
type type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="198f1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="198f1-107">Remarks</span></span>
<span data-ttu-id="198f1-108">Skróty typów umożliwia zapewniają bardziej zrozumiałej nazwy, aby poprawić czytelność kodu typu.</span><span class="sxs-lookup"><span data-stu-id="198f1-108">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="198f1-109">Ponadto można użyć do utworzenia łatwy w użyciu nazwy typu, który jest skomplikowane, aby zapisać. Ponadto można użyć skróty typów ułatwiające zmienić typu podstawowego bez zmieniania kodu, który używa typu.</span><span class="sxs-lookup"><span data-stu-id="198f1-109">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="198f1-110">Poniżej znajduje się skrót typu prostego.</span><span class="sxs-lookup"><span data-stu-id="198f1-110">The following is a simple type abbreviation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="198f1-111">Skróty typów mogą zawierać parametrów ogólnych, zgodnie z poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="198f1-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="198f1-112">W poprzednim kodzie `Transform` jest skrót typu, który reprezentuje funkcję, która pobiera jeden argument typu i która zwraca pojedynczą wartość tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="198f1-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="198f1-113">Skróty typów nie są zachowywane w kodzie programu .NET Framework MSIL.</span><span class="sxs-lookup"><span data-stu-id="198f1-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="198f1-114">W związku z tym gdy używasz zestawu F # z innego języka .NET Framework, należy użyć podstawowej nazwy typu dla skrót typu.</span><span class="sxs-lookup"><span data-stu-id="198f1-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="198f1-115">Skróty typów można również na jednostki miary.</span><span class="sxs-lookup"><span data-stu-id="198f1-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="198f1-116">Aby uzyskać więcej informacji, zobacz [jednostki miary](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="198f1-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="198f1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="198f1-117">See Also</span></span>
[<span data-ttu-id="198f1-118">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="198f1-118">F# Language Reference</span></span>](index.md)

