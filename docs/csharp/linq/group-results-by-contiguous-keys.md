---
title: Grupowanie wyników według ciągłych kluczy (LINQ w C#)
description: Jak grupowanie wyników według ciągłych kluczy za pomocą LINQ w C#.
ms.date: 08/14/2018
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: b5753c85bb07be4fc84b78a299eece961969ff9d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193008"
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="6e71f-103">Grupowanie wyników według ciągłych kluczy</span><span class="sxs-lookup"><span data-stu-id="6e71f-103">Group results by contiguous keys</span></span>

<span data-ttu-id="6e71f-104">Poniższy przykład pokazuje, jak należy zgrupować elementy na fragmenty, które reprezentują podciągów ciągłych kluczy.</span><span class="sxs-lookup"><span data-stu-id="6e71f-104">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="6e71f-105">Na przykład załóżmy, że podano następującej pary klucz wartość:</span><span class="sxs-lookup"><span data-stu-id="6e71f-105">For example, assume that you are given the following sequence of key-value pairs:</span></span>

|<span data-ttu-id="6e71f-106">Key</span><span class="sxs-lookup"><span data-stu-id="6e71f-106">Key</span></span>|<span data-ttu-id="6e71f-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="6e71f-107">Value</span></span>|
|---------|-----------|
|<span data-ttu-id="6e71f-108">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="6e71f-108">A</span></span>|<span data-ttu-id="6e71f-109">Firma Microsoft</span><span class="sxs-lookup"><span data-stu-id="6e71f-109">We</span></span>|
|<span data-ttu-id="6e71f-110">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="6e71f-110">A</span></span>|<span data-ttu-id="6e71f-111">namysłu</span><span class="sxs-lookup"><span data-stu-id="6e71f-111">think</span></span>|
|<span data-ttu-id="6e71f-112">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="6e71f-112">A</span></span>|<span data-ttu-id="6e71f-113">który</span><span class="sxs-lookup"><span data-stu-id="6e71f-113">that</span></span>|
|<span data-ttu-id="6e71f-114">B</span><span class="sxs-lookup"><span data-stu-id="6e71f-114">B</span></span>|<span data-ttu-id="6e71f-115">LINQ</span><span class="sxs-lookup"><span data-stu-id="6e71f-115">Linq</span></span>|
|<span data-ttu-id="6e71f-116">C</span><span class="sxs-lookup"><span data-stu-id="6e71f-116">C</span></span>|<span data-ttu-id="6e71f-117">is</span><span class="sxs-lookup"><span data-stu-id="6e71f-117">is</span></span>|
|<span data-ttu-id="6e71f-118">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="6e71f-118">A</span></span>|<span data-ttu-id="6e71f-119">tak naprawdę</span><span class="sxs-lookup"><span data-stu-id="6e71f-119">really</span></span>|
|<span data-ttu-id="6e71f-120">B</span><span class="sxs-lookup"><span data-stu-id="6e71f-120">B</span></span>|<span data-ttu-id="6e71f-121">chłodna</span><span class="sxs-lookup"><span data-stu-id="6e71f-121">cool</span></span>|
|<span data-ttu-id="6e71f-122">B</span><span class="sxs-lookup"><span data-stu-id="6e71f-122">B</span></span>|<span data-ttu-id="6e71f-123">!</span><span class="sxs-lookup"><span data-stu-id="6e71f-123">!</span></span>|

<span data-ttu-id="6e71f-124">Następujące grupy zostaną utworzone w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="6e71f-124">The following groups will be created in this order:</span></span>

1. <span data-ttu-id="6e71f-125">Uważamy, że</span><span class="sxs-lookup"><span data-stu-id="6e71f-125">We, think, that</span></span>

2. <span data-ttu-id="6e71f-126">LINQ</span><span class="sxs-lookup"><span data-stu-id="6e71f-126">Linq</span></span>

3. <span data-ttu-id="6e71f-127">is</span><span class="sxs-lookup"><span data-stu-id="6e71f-127">is</span></span>

4. <span data-ttu-id="6e71f-128">tak naprawdę</span><span class="sxs-lookup"><span data-stu-id="6e71f-128">really</span></span>

5. <span data-ttu-id="6e71f-129">chłodna!</span><span class="sxs-lookup"><span data-stu-id="6e71f-129">cool, !</span></span>

<span data-ttu-id="6e71f-130">Rozwiązanie jest implementowane jako metodę rozszerzenia, która jest bezpieczna dla wątków i który zwraca wyniki w sposób przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="6e71f-130">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="6e71f-131">Innymi słowy tworzy jej grup kiedy przesuwa się on przez sekwencję źródłową.</span><span class="sxs-lookup"><span data-stu-id="6e71f-131">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="6e71f-132">W odróżnieniu od `group` lub `orderby` operatorów, jego może rozpocząć zwracanie grup do obiektu wywołującego przed wszystkie sekwencji został odczytany.</span><span class="sxs-lookup"><span data-stu-id="6e71f-132">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>

<span data-ttu-id="6e71f-133">Bezpieczeństwo wątków odbywa się przez utworzenie kopii każdej grupy lub fragmentów, jak sekwencja źródłowa jest postanowiliśmy, zgodnie z objaśnieniem w komentarzach do kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="6e71f-133">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="6e71f-134">Jeśli sekwencja źródłowa jest duże sekwencję elementów sąsiadujących, środowisko uruchomieniowe języka wspólnego może zgłaszać <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="6e71f-134">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>

## <a name="example"></a><span data-ttu-id="6e71f-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="6e71f-135">Example</span></span>

<span data-ttu-id="6e71f-136">Poniższy kod przedstawia metody rozszerzenia i kod klienta, który korzysta z niego:</span><span class="sxs-lookup"><span data-stu-id="6e71f-136">The following example shows both the extension method and the client code that uses it:</span></span>

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

<span data-ttu-id="6e71f-137">Aby użyć metody rozszerzenia w projekcie, skopiuj `MyExtensions` klasy statycznej do nowego lub istniejącego źródła plik kodu i jeśli jest to konieczne, należy dodać `using` dyrektywy dla przestrzeni nazw, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="6e71f-137">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e71f-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e71f-138">See also</span></span>

- [<span data-ttu-id="6e71f-139">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="6e71f-139">Language Integrated Query (LINQ)</span></span>](index.md)
