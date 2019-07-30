---
title: Skróty typów
description: Dowiedz F# się więcej na temat skrótów typów, aby nadać typ bardziej zrozumiałej nazwy, aby ułatwić odczytywanie kodu.
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630211"
---
# <a name="type-abbreviations"></a><span data-ttu-id="a7b1a-103">Skróty typów</span><span class="sxs-lookup"><span data-stu-id="a7b1a-103">Type Abbreviations</span></span>

<span data-ttu-id="a7b1a-104">*Skrót typu* jest aliasem lub alternatywną nazwą typu.</span><span class="sxs-lookup"><span data-stu-id="a7b1a-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="a7b1a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7b1a-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="a7b1a-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7b1a-106">Remarks</span></span>

<span data-ttu-id="a7b1a-107">Można użyć skrótów typu, aby nadać typ bardziej zrozumiałą nazwę, aby ułatwić odczytywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="a7b1a-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="a7b1a-108">Można ich również użyć do utworzenia łatwej do użycia nazwy dla typu, który w przeciwnym razie jest nieskomplikowany. Ponadto można użyć skrótów typu, aby ułatwić zmianę typu podstawowego bez zmiany całego kodu, który używa tego typu.</span><span class="sxs-lookup"><span data-stu-id="a7b1a-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="a7b1a-109">Poniżej znajduje się prosty skrót typu.</span><span class="sxs-lookup"><span data-stu-id="a7b1a-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="a7b1a-110">Dostępność nazw skrótów typu jest domyślnie ustawiana na `public`.</span><span class="sxs-lookup"><span data-stu-id="a7b1a-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="a7b1a-111">Skróty typów mogą zawierać parametry ogólne, jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a7b1a-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="a7b1a-112">W poprzednim kodzie, `Transform` jest skrótem typu, który reprezentuje funkcję, która przyjmuje pojedynczy argument dowolnego typu, która zwraca pojedynczą wartość tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="a7b1a-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="a7b1a-113">Skróty typów nie są zachowywane w kodzie MSIL .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a7b1a-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="a7b1a-114">W związku z tym, jeśli F# używasz zestawu z innego języka .NET Framework, musisz użyć podstawowej nazwy typu dla skrótu typu.</span><span class="sxs-lookup"><span data-stu-id="a7b1a-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="a7b1a-115">Skróty typów mogą być również używane w jednostkach miary.</span><span class="sxs-lookup"><span data-stu-id="a7b1a-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="a7b1a-116">Aby uzyskać więcej informacji, zobacz [jednostki miary](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="a7b1a-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a7b1a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7b1a-117">See also</span></span>

- [<span data-ttu-id="a7b1a-118">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="a7b1a-118">F# Language Reference</span></span>](index.md)
