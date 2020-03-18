---
title: Grupowanie wyników według ciągłych kluczy (LINQ w języku C#)
description: Jak grupować wyniki według ciągłych kluczy przy użyciu LINQ w języku C#.
ms.date: 08/14/2018
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: b5753c85bb07be4fc84b78a299eece961969ff9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659907"
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="a9dae-103">Grupowanie wyników według ciągłych kluczy</span><span class="sxs-lookup"><span data-stu-id="a9dae-103">Group results by contiguous keys</span></span>

<span data-ttu-id="a9dae-104">W poniższym przykładzie pokazano, jak grupować elementy na fragmenty reprezentujące podsekwencje ciągłych kluczy.</span><span class="sxs-lookup"><span data-stu-id="a9dae-104">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="a9dae-105">Załóżmy na przykład, że podano następującą sekwencję par klucz-wartość:</span><span class="sxs-lookup"><span data-stu-id="a9dae-105">For example, assume that you are given the following sequence of key-value pairs:</span></span>

|<span data-ttu-id="a9dae-106">Klucz</span><span class="sxs-lookup"><span data-stu-id="a9dae-106">Key</span></span>|<span data-ttu-id="a9dae-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="a9dae-107">Value</span></span>|
|---------|-----------|
|<span data-ttu-id="a9dae-108">A</span><span class="sxs-lookup"><span data-stu-id="a9dae-108">A</span></span>|<span data-ttu-id="a9dae-109">My</span><span class="sxs-lookup"><span data-stu-id="a9dae-109">We</span></span>|
|<span data-ttu-id="a9dae-110">A</span><span class="sxs-lookup"><span data-stu-id="a9dae-110">A</span></span>|<span data-ttu-id="a9dae-111">Myśleć</span><span class="sxs-lookup"><span data-stu-id="a9dae-111">think</span></span>|
|<span data-ttu-id="a9dae-112">A</span><span class="sxs-lookup"><span data-stu-id="a9dae-112">A</span></span>|<span data-ttu-id="a9dae-113">Że</span><span class="sxs-lookup"><span data-stu-id="a9dae-113">that</span></span>|
|<span data-ttu-id="a9dae-114">B</span><span class="sxs-lookup"><span data-stu-id="a9dae-114">B</span></span>|<span data-ttu-id="a9dae-115">Linq</span><span class="sxs-lookup"><span data-stu-id="a9dae-115">Linq</span></span>|
|<span data-ttu-id="a9dae-116">C</span><span class="sxs-lookup"><span data-stu-id="a9dae-116">C</span></span>|<span data-ttu-id="a9dae-117">is</span><span class="sxs-lookup"><span data-stu-id="a9dae-117">is</span></span>|
|<span data-ttu-id="a9dae-118">A</span><span class="sxs-lookup"><span data-stu-id="a9dae-118">A</span></span>|<span data-ttu-id="a9dae-119">Naprawdę</span><span class="sxs-lookup"><span data-stu-id="a9dae-119">really</span></span>|
|<span data-ttu-id="a9dae-120">B</span><span class="sxs-lookup"><span data-stu-id="a9dae-120">B</span></span>|<span data-ttu-id="a9dae-121">Cool</span><span class="sxs-lookup"><span data-stu-id="a9dae-121">cool</span></span>|
|<span data-ttu-id="a9dae-122">B</span><span class="sxs-lookup"><span data-stu-id="a9dae-122">B</span></span>|<span data-ttu-id="a9dae-123">!</span><span class="sxs-lookup"><span data-stu-id="a9dae-123">!</span></span>|

<span data-ttu-id="a9dae-124">W następującej kolejności zostaną utworzone następujące grupy:</span><span class="sxs-lookup"><span data-stu-id="a9dae-124">The following groups will be created in this order:</span></span>

1. <span data-ttu-id="a9dae-125">My, myślimy, że</span><span class="sxs-lookup"><span data-stu-id="a9dae-125">We, think, that</span></span>

2. <span data-ttu-id="a9dae-126">Linq</span><span class="sxs-lookup"><span data-stu-id="a9dae-126">Linq</span></span>

3. <span data-ttu-id="a9dae-127">is</span><span class="sxs-lookup"><span data-stu-id="a9dae-127">is</span></span>

4. <span data-ttu-id="a9dae-128">Naprawdę</span><span class="sxs-lookup"><span data-stu-id="a9dae-128">really</span></span>

5. <span data-ttu-id="a9dae-129">Cool!</span><span class="sxs-lookup"><span data-stu-id="a9dae-129">cool, !</span></span>

<span data-ttu-id="a9dae-130">Rozwiązanie jest implementowane jako metoda rozszerzenia, która jest bezpieczna dla wątków i która zwraca jego wyniki w sposób przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="a9dae-130">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="a9dae-131">Innymi słowy, tworzy swoje grupy, gdy porusza się po sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="a9dae-131">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="a9dae-132">W `group` przeciwieństwie `orderby` do lub operatorów można rozpocząć zwracanie grup do obiektu wywołującego przed wszystkie sekwencji został odczytany.</span><span class="sxs-lookup"><span data-stu-id="a9dae-132">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>

<span data-ttu-id="a9dae-133">Bezpieczeństwo wątków jest realizowane przez wykonanie kopii każdej grupy lub fragmentu jako sekwencji źródłowej jest iterowana, jak wyjaśniono w komentarzach kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="a9dae-133">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="a9dae-134">Jeśli sekwencja źródłowa ma dużą sekwencję sąsiadujących elementów, czas <xref:System.OutOfMemoryException>wykonywania języka wspólnego może zgłosić plik .</span><span class="sxs-lookup"><span data-stu-id="a9dae-134">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>

## <a name="example"></a><span data-ttu-id="a9dae-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9dae-135">Example</span></span>

<span data-ttu-id="a9dae-136">W poniższym przykładzie pokazano zarówno metodę rozszerzenia, jak i kod klienta, który go używa:</span><span class="sxs-lookup"><span data-stu-id="a9dae-136">The following example shows both the extension method and the client code that uses it:</span></span>

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

<span data-ttu-id="a9dae-137">Aby użyć metody rozszerzenia w projekcie, skopiuj `MyExtensions` klasę statyczną do nowego lub `using` istniejącego pliku kodu źródłowego, a jeśli jest to wymagane, dodaj dyrektywę dla obszaru nazw, w którym się znajduje.</span><span class="sxs-lookup"><span data-stu-id="a9dae-137">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9dae-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9dae-138">See also</span></span>

- [<span data-ttu-id="a9dae-139">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="a9dae-139">Language Integrated Query (LINQ)</span></span>](index.md)
