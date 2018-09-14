---
title: Grupowanie wyników według ciągłych kluczy (LINQ w C#)
description: Jak grupowanie wyników według ciągłych kluczy za pomocą LINQ w C#.
ms.date: 08/14/2018
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: b5753c85bb07be4fc84b78a299eece961969ff9d
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527009"
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="d6d10-103">Grupowanie wyników według ciągłych kluczy</span><span class="sxs-lookup"><span data-stu-id="d6d10-103">Group results by contiguous keys</span></span>

<span data-ttu-id="d6d10-104">Poniższy przykład pokazuje, jak należy zgrupować elementy na fragmenty, które reprezentują podciągów ciągłych kluczy.</span><span class="sxs-lookup"><span data-stu-id="d6d10-104">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="d6d10-105">Na przykład załóżmy, że podano następującej pary klucz wartość:</span><span class="sxs-lookup"><span data-stu-id="d6d10-105">For example, assume that you are given the following sequence of key-value pairs:</span></span>

|<span data-ttu-id="d6d10-106">Key</span><span class="sxs-lookup"><span data-stu-id="d6d10-106">Key</span></span>|<span data-ttu-id="d6d10-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="d6d10-107">Value</span></span>|
|---------|-----------|
|<span data-ttu-id="d6d10-108">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="d6d10-108">A</span></span>|<span data-ttu-id="d6d10-109">Firma Microsoft</span><span class="sxs-lookup"><span data-stu-id="d6d10-109">We</span></span>|
|<span data-ttu-id="d6d10-110">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="d6d10-110">A</span></span>|<span data-ttu-id="d6d10-111">namysłu</span><span class="sxs-lookup"><span data-stu-id="d6d10-111">think</span></span>|
|<span data-ttu-id="d6d10-112">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="d6d10-112">A</span></span>|<span data-ttu-id="d6d10-113">który</span><span class="sxs-lookup"><span data-stu-id="d6d10-113">that</span></span>|
|<span data-ttu-id="d6d10-114">B</span><span class="sxs-lookup"><span data-stu-id="d6d10-114">B</span></span>|<span data-ttu-id="d6d10-115">LINQ</span><span class="sxs-lookup"><span data-stu-id="d6d10-115">Linq</span></span>|
|<span data-ttu-id="d6d10-116">C</span><span class="sxs-lookup"><span data-stu-id="d6d10-116">C</span></span>|<span data-ttu-id="d6d10-117">is</span><span class="sxs-lookup"><span data-stu-id="d6d10-117">is</span></span>|
|<span data-ttu-id="d6d10-118">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="d6d10-118">A</span></span>|<span data-ttu-id="d6d10-119">tak naprawdę</span><span class="sxs-lookup"><span data-stu-id="d6d10-119">really</span></span>|
|<span data-ttu-id="d6d10-120">B</span><span class="sxs-lookup"><span data-stu-id="d6d10-120">B</span></span>|<span data-ttu-id="d6d10-121">chłodna</span><span class="sxs-lookup"><span data-stu-id="d6d10-121">cool</span></span>|
|<span data-ttu-id="d6d10-122">B</span><span class="sxs-lookup"><span data-stu-id="d6d10-122">B</span></span>|<span data-ttu-id="d6d10-123">!</span><span class="sxs-lookup"><span data-stu-id="d6d10-123">!</span></span>|

<span data-ttu-id="d6d10-124">Następujące grupy zostaną utworzone w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="d6d10-124">The following groups will be created in this order:</span></span>

1. <span data-ttu-id="d6d10-125">Uważamy, że</span><span class="sxs-lookup"><span data-stu-id="d6d10-125">We, think, that</span></span>

2. <span data-ttu-id="d6d10-126">LINQ</span><span class="sxs-lookup"><span data-stu-id="d6d10-126">Linq</span></span>

3. <span data-ttu-id="d6d10-127">is</span><span class="sxs-lookup"><span data-stu-id="d6d10-127">is</span></span>

4. <span data-ttu-id="d6d10-128">tak naprawdę</span><span class="sxs-lookup"><span data-stu-id="d6d10-128">really</span></span>

5. <span data-ttu-id="d6d10-129">chłodna!</span><span class="sxs-lookup"><span data-stu-id="d6d10-129">cool, !</span></span>

<span data-ttu-id="d6d10-130">Rozwiązanie jest implementowane jako metodę rozszerzenia, która jest bezpieczna dla wątków i który zwraca wyniki w sposób przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="d6d10-130">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="d6d10-131">Innymi słowy tworzy jej grup kiedy przesuwa się on przez sekwencję źródłową.</span><span class="sxs-lookup"><span data-stu-id="d6d10-131">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="d6d10-132">W odróżnieniu od `group` lub `orderby` operatorów, jego może rozpocząć zwracanie grup do obiektu wywołującego przed wszystkie sekwencji został odczytany.</span><span class="sxs-lookup"><span data-stu-id="d6d10-132">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>

<span data-ttu-id="d6d10-133">Bezpieczeństwo wątków odbywa się przez utworzenie kopii każdej grupy lub fragmentów, jak sekwencja źródłowa jest postanowiliśmy, zgodnie z objaśnieniem w komentarzach do kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d6d10-133">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="d6d10-134">Jeśli sekwencja źródłowa jest duże sekwencję elementów sąsiadujących, środowisko uruchomieniowe języka wspólnego może zgłaszać <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="d6d10-134">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>

## <a name="example"></a><span data-ttu-id="d6d10-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6d10-135">Example</span></span>

<span data-ttu-id="d6d10-136">Poniższy kod przedstawia metody rozszerzenia i kod klienta, który korzysta z niego:</span><span class="sxs-lookup"><span data-stu-id="d6d10-136">The following example shows both the extension method and the client code that uses it:</span></span>

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

<span data-ttu-id="d6d10-137">Aby użyć metody rozszerzenia w projekcie, skopiuj `MyExtensions` klasy statycznej do nowego lub istniejącego źródła plik kodu i jeśli jest to konieczne, należy dodać `using` dyrektywy dla przestrzeni nazw, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="d6d10-137">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6d10-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6d10-138">See also</span></span>

- [<span data-ttu-id="d6d10-139">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d6d10-139">Language Integrated Query (LINQ)</span></span>](index.md)
