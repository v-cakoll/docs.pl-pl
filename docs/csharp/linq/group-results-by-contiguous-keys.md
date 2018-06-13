---
title: Grupy wyników według ciągłych kluczy
description: Jak grupowanie wyników według ciągłych kluczy.
ms.date: 12/1/2016
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: a8d6ac133932a12154d5b23454065144c7652067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281440"
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="57421-103">Grupy wyników według ciągłych kluczy</span><span class="sxs-lookup"><span data-stu-id="57421-103">Group results by contiguous keys</span></span>

<span data-ttu-id="57421-104">Poniższy przykład przedstawia sposób grupowania elementów na fragmenty, które reprezentują podciągów ciągłych kluczy.</span><span class="sxs-lookup"><span data-stu-id="57421-104">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="57421-105">Załóżmy na przykład, zostanie wyświetlony następujący ciąg par klucz wartość:</span><span class="sxs-lookup"><span data-stu-id="57421-105">For example, assume that you are given the following sequence of key-value pairs:</span></span>  
  
|<span data-ttu-id="57421-106">Key</span><span class="sxs-lookup"><span data-stu-id="57421-106">Key</span></span>|<span data-ttu-id="57421-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="57421-107">Value</span></span>|  
|---------|-----------|  
|<span data-ttu-id="57421-108">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="57421-108">A</span></span>|<span data-ttu-id="57421-109">Firma Microsoft</span><span class="sxs-lookup"><span data-stu-id="57421-109">We</span></span>|  
|<span data-ttu-id="57421-110">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="57421-110">A</span></span>|<span data-ttu-id="57421-111">Pomyśl</span><span class="sxs-lookup"><span data-stu-id="57421-111">think</span></span>|  
|<span data-ttu-id="57421-112">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="57421-112">A</span></span>|<span data-ttu-id="57421-113">który</span><span class="sxs-lookup"><span data-stu-id="57421-113">that</span></span>|  
|<span data-ttu-id="57421-114">B</span><span class="sxs-lookup"><span data-stu-id="57421-114">B</span></span>|<span data-ttu-id="57421-115">LINQ</span><span class="sxs-lookup"><span data-stu-id="57421-115">Linq</span></span>|  
|<span data-ttu-id="57421-116">C</span><span class="sxs-lookup"><span data-stu-id="57421-116">C</span></span>|<span data-ttu-id="57421-117">is</span><span class="sxs-lookup"><span data-stu-id="57421-117">is</span></span>|  
|<span data-ttu-id="57421-118">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="57421-118">A</span></span>|<span data-ttu-id="57421-119">naprawdę</span><span class="sxs-lookup"><span data-stu-id="57421-119">really</span></span>|  
|<span data-ttu-id="57421-120">B</span><span class="sxs-lookup"><span data-stu-id="57421-120">B</span></span>|<span data-ttu-id="57421-121">Cool</span><span class="sxs-lookup"><span data-stu-id="57421-121">cool</span></span>|  
|<span data-ttu-id="57421-122">B</span><span class="sxs-lookup"><span data-stu-id="57421-122">B</span></span>|<span data-ttu-id="57421-123">!</span><span class="sxs-lookup"><span data-stu-id="57421-123">!</span></span>|  
  
 <span data-ttu-id="57421-124">Następujące grupy zostanie utworzony w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="57421-124">The following groups will be created in this order:</span></span>  
  
1.  <span data-ttu-id="57421-125">Firma Microsoft, wziąć pod uwagę, że</span><span class="sxs-lookup"><span data-stu-id="57421-125">We, think, that</span></span>  
  
2.  <span data-ttu-id="57421-126">LINQ</span><span class="sxs-lookup"><span data-stu-id="57421-126">Linq</span></span>  
  
3.  <span data-ttu-id="57421-127">is</span><span class="sxs-lookup"><span data-stu-id="57421-127">is</span></span>  
  
4.  <span data-ttu-id="57421-128">naprawdę</span><span class="sxs-lookup"><span data-stu-id="57421-128">really</span></span>  
  
5.  <span data-ttu-id="57421-129">Cool!</span><span class="sxs-lookup"><span data-stu-id="57421-129">cool, !</span></span>  
  
 <span data-ttu-id="57421-130">Rozwiązanie jest implementowany jako metodę rozszerzenia, który jest wątkowo i które zwraca wyniki w sposób przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="57421-130">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="57421-131">Innymi słowy tworzy jej grup przesyłane za pośrednictwem sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="57421-131">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="57421-132">W odróżnieniu od `group` lub `orderby` operatorów, jego można rozpocząć zwracanie grupy do obiektu wywołującego przed wszystkie sekwencji została przeczytana.</span><span class="sxs-lookup"><span data-stu-id="57421-132">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>  
  
 <span data-ttu-id="57421-133">Bezpieczeństwo wątków jest realizowane przez utworzenie kopii każdej grupy lub fragmentu, jak sekwencji źródłowej jest iterowane, zgodnie z objaśnieniem w komentarze w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="57421-133">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="57421-134">Jeśli sekwencji źródłowej ma duże sekwencję elementów ciągły, środowisko uruchomieniowe języka wspólnego może zgłaszać <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="57421-134">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57421-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="57421-135">Example</span></span>  
 <span data-ttu-id="57421-136">W poniższym przykładzie pokazano zarówno metodę rozszerzenia, jak i kodu klienta, który korzysta z niego.</span><span class="sxs-lookup"><span data-stu-id="57421-136">The following example shows both the extension method and the client code that uses it.</span></span>  
  
 [!code-csharp[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 <span data-ttu-id="57421-137">Aby używać metody rozszerzenia w projekcie, skopiuj `MyExtensions` klasy statycznej do nowego lub istniejącego źródła code pliku i w razie potrzeby, Dodaj `using` dyrektywy dla przestrzeni nazw, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="57421-137">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57421-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57421-138">See also</span></span>  
 [<span data-ttu-id="57421-139">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="57421-139">LINQ Query Expressions</span></span>](index.md)  
 
