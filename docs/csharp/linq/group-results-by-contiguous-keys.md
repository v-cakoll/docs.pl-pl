---
title: "Grupy wyników według ciągłych kluczy"
description: "Jak grupowanie wyników według ciągłych kluczy."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: cdd06a6fad037291bbc5aa011b47bb668fa2f062
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="30166-104">Grupy wyników według ciągłych kluczy</span><span class="sxs-lookup"><span data-stu-id="30166-104">Group results by contiguous keys</span></span>

<span data-ttu-id="30166-105">Poniższy przykład przedstawia sposób grupowania elementów na fragmenty, które reprezentują podciągów ciągłych kluczy.</span><span class="sxs-lookup"><span data-stu-id="30166-105">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="30166-106">Załóżmy na przykład, zostanie wyświetlony następujący ciąg par klucz wartość:</span><span class="sxs-lookup"><span data-stu-id="30166-106">For example, assume that you are given the following sequence of key-value pairs:</span></span>  
  
|<span data-ttu-id="30166-107">Key</span><span class="sxs-lookup"><span data-stu-id="30166-107">Key</span></span>|<span data-ttu-id="30166-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="30166-108">Value</span></span>|  
|---------|-----------|  
|<span data-ttu-id="30166-109">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="30166-109">A</span></span>|<span data-ttu-id="30166-110">Firma Microsoft</span><span class="sxs-lookup"><span data-stu-id="30166-110">We</span></span>|  
|<span data-ttu-id="30166-111">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="30166-111">A</span></span>|<span data-ttu-id="30166-112">Pomyśl</span><span class="sxs-lookup"><span data-stu-id="30166-112">think</span></span>|  
|<span data-ttu-id="30166-113">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="30166-113">A</span></span>|<span data-ttu-id="30166-114">który</span><span class="sxs-lookup"><span data-stu-id="30166-114">that</span></span>|  
|<span data-ttu-id="30166-115">B</span><span class="sxs-lookup"><span data-stu-id="30166-115">B</span></span>|<span data-ttu-id="30166-116">LINQ</span><span class="sxs-lookup"><span data-stu-id="30166-116">Linq</span></span>|  
|<span data-ttu-id="30166-117">C</span><span class="sxs-lookup"><span data-stu-id="30166-117">C</span></span>|<span data-ttu-id="30166-118">is</span><span class="sxs-lookup"><span data-stu-id="30166-118">is</span></span>|  
|<span data-ttu-id="30166-119">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="30166-119">A</span></span>|<span data-ttu-id="30166-120">naprawdę</span><span class="sxs-lookup"><span data-stu-id="30166-120">really</span></span>|  
|<span data-ttu-id="30166-121">B</span><span class="sxs-lookup"><span data-stu-id="30166-121">B</span></span>|<span data-ttu-id="30166-122">Cool</span><span class="sxs-lookup"><span data-stu-id="30166-122">cool</span></span>|  
|<span data-ttu-id="30166-123">B</span><span class="sxs-lookup"><span data-stu-id="30166-123">B</span></span>|<span data-ttu-id="30166-124">!</span><span class="sxs-lookup"><span data-stu-id="30166-124">!</span></span>|  
  
 <span data-ttu-id="30166-125">Następujące grupy zostanie utworzony w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="30166-125">The following groups will be created in this order:</span></span>  
  
1.  <span data-ttu-id="30166-126">Firma Microsoft, wziąć pod uwagę, że</span><span class="sxs-lookup"><span data-stu-id="30166-126">We, think, that</span></span>  
  
2.  <span data-ttu-id="30166-127">LINQ</span><span class="sxs-lookup"><span data-stu-id="30166-127">Linq</span></span>  
  
3.  <span data-ttu-id="30166-128">is</span><span class="sxs-lookup"><span data-stu-id="30166-128">is</span></span>  
  
4.  <span data-ttu-id="30166-129">naprawdę</span><span class="sxs-lookup"><span data-stu-id="30166-129">really</span></span>  
  
5.  <span data-ttu-id="30166-130">Cool!</span><span class="sxs-lookup"><span data-stu-id="30166-130">cool, !</span></span>  
  
 <span data-ttu-id="30166-131">Rozwiązanie jest implementowany jako metodę rozszerzenia, który jest wątkowo i które zwraca wyniki w sposób przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="30166-131">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="30166-132">Innymi słowy tworzy jej grup przesyłane za pośrednictwem sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="30166-132">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="30166-133">W odróżnieniu od `group` lub `orderby` operatorów, jego można rozpocząć zwracanie grupy do obiektu wywołującego przed wszystkie sekwencji została przeczytana.</span><span class="sxs-lookup"><span data-stu-id="30166-133">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>  
  
 <span data-ttu-id="30166-134">Bezpieczeństwo wątków jest realizowane przez utworzenie kopii każdej grupy lub fragmentu, jak sekwencji źródłowej jest iterowane, zgodnie z objaśnieniem w komentarze w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="30166-134">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="30166-135">Jeśli sekwencji źródłowej ma duże sekwencję elementów ciągły, środowisko uruchomieniowe języka wspólnego może zgłaszać <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="30166-135">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30166-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="30166-136">Example</span></span>  
 <span data-ttu-id="30166-137">W poniższym przykładzie pokazano zarówno metodę rozszerzenia, jak i kodu klienta, który korzysta z niego.</span><span class="sxs-lookup"><span data-stu-id="30166-137">The following example shows both the extension method and the client code that uses it.</span></span>  
  
 [!code-csharp[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 <span data-ttu-id="30166-138">Aby używać metody rozszerzenia w projekcie, skopiuj `MyExtensions` klasy statycznej do nowego lub istniejącego źródła code pliku i w razie potrzeby, Dodaj `using` dyrektywy dla przestrzeni nazw, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="30166-138">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30166-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30166-139">See also</span></span>  
 [<span data-ttu-id="30166-140">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="30166-140">LINQ Query Expressions</span></span>](index.md)  
 
