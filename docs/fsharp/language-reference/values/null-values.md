---
title: "Wartości zerowe (F#)"
description: "Dowiedz się, jak używana jest wartość null w języku programowania w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 68ebd261-51cf-4582-b2dc-44c84d1c2500
ms.openlocfilehash: 01c14de00eb5efd0952145ffc8aabe69d65a3a48
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="null-values"></a><span data-ttu-id="a6465-104">Wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="a6465-104">Null Values</span></span>

<span data-ttu-id="a6465-105">W tym temacie opisano, jak wartość null jest używana w języku F #.</span><span class="sxs-lookup"><span data-stu-id="a6465-105">This topic describes how the null value is used in F#.</span></span>


## <a name="null-value"></a><span data-ttu-id="a6465-106">Wartość null</span><span class="sxs-lookup"><span data-stu-id="a6465-106">Null Value</span></span>
<span data-ttu-id="a6465-107">Wartość null jest zwykle nieużywane w języku F # dla wartości lub zmienne.</span><span class="sxs-lookup"><span data-stu-id="a6465-107">The null value is not normally used in F# for values or variables.</span></span> <span data-ttu-id="a6465-108">Jednak null pojawia się jako nieprawidłowej wartości w niektórych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="a6465-108">However, null appears as an abnormal value in certain situations.</span></span> <span data-ttu-id="a6465-109">Jeśli typ jest zdefiniowany w języku F #, wartość null nie jest dozwolona jako standardowa, chyba że [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) atrybut jest stosowany do typu.</span><span class="sxs-lookup"><span data-stu-id="a6465-109">If a type is defined in F#, null is not permitted as a regular value unless the [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) attribute is applied to the type.</span></span> <span data-ttu-id="a6465-110">Jeśli typ jest zdefiniowany w innym języku .NET, wartość null jest możliwą wartość, a gdy współdziałania takich typów, mogą występować w kodzie języka F # wartości null.</span><span class="sxs-lookup"><span data-stu-id="a6465-110">If a type is defined in some other .NET language, null is a possible value, and when you are interoperating with such types, your F# code might encounter null values.</span></span>

<span data-ttu-id="a6465-111">Typ zdefiniowany w języku F # i używane wyłącznie z języka F #, jedynym sposobem, aby utworzyć wartość null, bezpośrednio za pomocą biblioteki F # jest użycie [unchecked.defaultof —](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) lub [Array.zerocreate —](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2).</span><span class="sxs-lookup"><span data-stu-id="a6465-111">For a type defined in F# and used strictly from F#, the only way to create a null value using the F# library directly is to use [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) or [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2).</span></span> <span data-ttu-id="a6465-112">Dla typu F # używany z innymi językami .NET, lub, jeśli używasz tego typu z interfejsu API, który nie jest napisany w języku F #, takich jak .NET Framework, może wystąpić wartości null.</span><span class="sxs-lookup"><span data-stu-id="a6465-112">However, for an F# type that is used from other .NET languages, or if you are using that type with an API that is not written in F#, such as the .NET Framework, null values can occur.</span></span>

<span data-ttu-id="a6465-113">Można użyć `option` typu w języku F # podczas może użyć zmiennej odwołania o możliwych wartości null w innym języku .NET.</span><span class="sxs-lookup"><span data-stu-id="a6465-113">You can use the `option` type in F# when you might use a reference variable with a possible null value in another .NET language.</span></span> <span data-ttu-id="a6465-114">Zamiast wartości null w języku F # `option` typu, możesz użyć wartości opcji `None` Jeśli nie ma żadnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a6465-114">Instead of null, with an F# `option` type, you use the option value `None` if there is no object.</span></span> <span data-ttu-id="a6465-115">Użyj wartości opcji `Some(obj)` z obiektem `obj` po obiektu.</span><span class="sxs-lookup"><span data-stu-id="a6465-115">You use the option value `Some(obj)` with an object `obj` when there is an object.</span></span> <span data-ttu-id="a6465-116">Aby uzyskać więcej informacji, zobacz [opcje](../options.md).</span><span class="sxs-lookup"><span data-stu-id="a6465-116">For more information, see [Options](../options.md).</span></span>

<span data-ttu-id="a6465-117">`null` — Słowo kluczowe jest nieprawidłowy — słowo kluczowe w języku F # i należy go używać w przypadku korzystania z interfejsów API architektury .NET Framework lub innych interfejsów API, które są zapisywane w innym języku .NET.</span><span class="sxs-lookup"><span data-stu-id="a6465-117">The `null` keyword is a valid keyword in the F# language, and you have to use it when you are working with .NET Framework APIs or other APIs that are written in another .NET language.</span></span> <span data-ttu-id="a6465-118">Dwie sytuacje, w których może być konieczne wartości null są wywołać interfejs API .NET i przekazać wartość null jako argumentu i interpretowania wartości zwracanej lub parametru wyjściowego po wywołaniu metody .NET.</span><span class="sxs-lookup"><span data-stu-id="a6465-118">The two situations in which you might need a null value are when you call a .NET API and pass a null value as an argument, and when you interpret the return value or an output parameter from a .NET method call.</span></span>

<span data-ttu-id="a6465-119">Aby przekazać wartości null do metody .NET, wystarczy użyć `null` — słowo kluczowe w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a6465-119">To pass a null value to a .NET method, just use the `null` keyword in the calling code.</span></span> <span data-ttu-id="a6465-120">Pokazano to w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="a6465-120">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

<span data-ttu-id="a6465-121">Aby zinterpretować wartość null, uzyskany z metody .NET, użyj wzorca dopasowania, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="a6465-121">To interpret a null value that is obtained from a .NET method, use pattern matching if you can.</span></span> <span data-ttu-id="a6465-122">Poniższy przykładowy kod przedstawia użycie dopasowanie wzorca, aby zinterpretować wartość null, która jest zwracana z `ReadLine` podczas próby odczytu poza końcem strumienia wejściowego.</span><span class="sxs-lookup"><span data-stu-id="a6465-122">The following code example shows how to use pattern matching to interpret the null value that is returned from `ReadLine` when it tries to read past the end of an input stream.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

<span data-ttu-id="a6465-123">Wartości null dla typów F # może być również generowany w inny sposób, na przykład przy użyciu `Array.zeroCreate`, które wywołuje `Unchecked.defaultof`.</span><span class="sxs-lookup"><span data-stu-id="a6465-123">Null values for F# types can also be generated in other ways, such as when you use `Array.zeroCreate`, which calls `Unchecked.defaultof`.</span></span> <span data-ttu-id="a6465-124">Należy zachować ostrożność przy taki kod, aby zachować wartości null hermetyzowany.</span><span class="sxs-lookup"><span data-stu-id="a6465-124">You must be careful with such code to keep the null values encapsulated.</span></span> <span data-ttu-id="a6465-125">W bibliotece przeznaczone tylko do F # nie masz do sprawdzenia wartości null w każdej funkcji.</span><span class="sxs-lookup"><span data-stu-id="a6465-125">In a library intended only for F#, you do not have to check for null values in every function.</span></span> <span data-ttu-id="a6465-126">Jeśli piszesz biblioteki współdziałanie z innymi językami .NET, może być konieczne Dodaj sprawdza, czy wartości null parametrów wejściowych i zgłosić `ArgumentNullException`, tak jak w kodzie C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a6465-126">If you are writing a library for interoperation with other .NET languages, you might have to add checks for null input parameters and throw an `ArgumentNullException`, just as you do in C# or Visual Basic code.</span></span>

<span data-ttu-id="a6465-127">Poniższy kod służy do sprawdzania, jeśli wartość dowolnego ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="a6465-127">You can use the following code to check if an arbitrary value is null.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a><span data-ttu-id="a6465-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6465-128">See Also</span></span>
[<span data-ttu-id="a6465-129">Wartości</span><span class="sxs-lookup"><span data-stu-id="a6465-129">Values</span></span>](index.md)

[<span data-ttu-id="a6465-130">Wyrażenia dopasowania</span><span class="sxs-lookup"><span data-stu-id="a6465-130">Match Expressions</span></span>](../match-expressions.md)
