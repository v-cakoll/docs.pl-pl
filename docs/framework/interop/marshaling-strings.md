---
title: "Marshaling ciągów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4d53cd4072ab3f9ff52729f122c0a0ecab400df
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="marshaling-strings"></a><span data-ttu-id="f432a-102">Marshaling ciągów</span><span class="sxs-lookup"><span data-stu-id="f432a-102">Marshaling Strings</span></span>
<span data-ttu-id="f432a-103">Wywołanie platformy parametrów ciągu kopie, konwersję z formatu .NET Framework (Unicode) do formatu niezarządzane (ANSI), jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="f432a-103">Platform invoke copies string parameters, converting them from the .NET Framework format (Unicode) to the unmanaged format (ANSI), if needed.</span></span> <span data-ttu-id="f432a-104">Ponieważ ciągi zarządzane są niezmienne, wywołanie platformy nie kopiuje je ponownie w pamięci niezarządzanej pamięci zarządzanej po powrocie z funkcji.</span><span class="sxs-lookup"><span data-stu-id="f432a-104">Because managed strings are immutable, platform invoke does not copy them back from unmanaged memory to managed memory when the function returns.</span></span>  
  
 <span data-ttu-id="f432a-105">Poniższej tabeli wymieniono opcje marshaling dla ciągów, w tym artykule opisano sposób ich użycia i Link do odpowiedniego próbki .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f432a-105">The following table lists marshaling options for strings, describes their usage, and provides a link to the corresponding .NET Framework sample.</span></span>  
  
|<span data-ttu-id="f432a-106">String</span><span class="sxs-lookup"><span data-stu-id="f432a-106">String</span></span>|<span data-ttu-id="f432a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f432a-107">Description</span></span>|<span data-ttu-id="f432a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="f432a-108">Sample</span></span>|  
|------------|-----------------|------------|  
|<span data-ttu-id="f432a-109">Według wartości.</span><span class="sxs-lookup"><span data-stu-id="f432a-109">By value.</span></span>|<span data-ttu-id="f432a-110">Przekazuje ciągów, tak jak parametry.</span><span class="sxs-lookup"><span data-stu-id="f432a-110">Passes strings as In parameters.</span></span>|[<span data-ttu-id="f432a-111">MsgBox</span><span class="sxs-lookup"><span data-stu-id="f432a-111">MsgBox</span></span>](../../../docs/framework/interop/msgbox-sample.md)|  
|<span data-ttu-id="f432a-112">W wyniku.</span><span class="sxs-lookup"><span data-stu-id="f432a-112">As result.</span></span>|<span data-ttu-id="f432a-113">Zwraca ciągów z kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="f432a-113">Returns strings from unmanaged code.</span></span>|[<span data-ttu-id="f432a-114">Ciągi</span><span class="sxs-lookup"><span data-stu-id="f432a-114">Strings</span></span>](http://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|<span data-ttu-id="f432a-115">Przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f432a-115">By reference.</span></span>|<span data-ttu-id="f432a-116">Przekazuje ciągi jako We/Wy przy użyciu parametrów <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="f432a-116">Passes strings as In/Out parameters using <xref:System.Text.StringBuilder>.</span></span>|[<span data-ttu-id="f432a-117">Buforów</span><span class="sxs-lookup"><span data-stu-id="f432a-117">Buffers</span></span>](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|<span data-ttu-id="f432a-118">W strukturze przez wartość.</span><span class="sxs-lookup"><span data-stu-id="f432a-118">In a structure by value.</span></span>|<span data-ttu-id="f432a-119">Przekazuje ciągów w strukturze jest parametrem In.</span><span class="sxs-lookup"><span data-stu-id="f432a-119">Passes strings in a structure that is an In parameter.</span></span>|[<span data-ttu-id="f432a-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="f432a-120">Structs</span></span>](http://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|<span data-ttu-id="f432a-121">W strukturze przez odwołanie **(char\*)**.</span><span class="sxs-lookup"><span data-stu-id="f432a-121">In a structure by reference **(char\*)**.</span></span>|<span data-ttu-id="f432a-122">Przekazuje ciągów w strukturze jest parametrem we/wy.</span><span class="sxs-lookup"><span data-stu-id="f432a-122">Passes strings in a structure that is an In/Out parameter.</span></span> <span data-ttu-id="f432a-123">Funkcji niezarządzanej oczekuje wskaźnika do buforu znaków, a rozmiar buforu jest elementem członkowskim struktury.</span><span class="sxs-lookup"><span data-stu-id="f432a-123">The unmanaged function expects a pointer to a character buffer and the buffer size is a member of the structure.</span></span>|[<span data-ttu-id="f432a-124">Ciągi</span><span class="sxs-lookup"><span data-stu-id="f432a-124">Strings</span></span>](http://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|<span data-ttu-id="f432a-125">W strukturze przez odwołanie **(char[])**.</span><span class="sxs-lookup"><span data-stu-id="f432a-125">In a structure by reference **(char[])**.</span></span>|<span data-ttu-id="f432a-126">Przekazuje ciągów w strukturze jest parametrem we/wy.</span><span class="sxs-lookup"><span data-stu-id="f432a-126">Passes strings in a structure that is an In/Out parameter.</span></span> <span data-ttu-id="f432a-127">Funkcji niezarządzanej oczekuje bufor osadzonych znaków.</span><span class="sxs-lookup"><span data-stu-id="f432a-127">The unmanaged function expects an embedded character buffer.</span></span>|[<span data-ttu-id="f432a-128">OSInfo</span><span class="sxs-lookup"><span data-stu-id="f432a-128">OSInfo</span></span>](http://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455)|  
|<span data-ttu-id="f432a-129">W klasie przez wartość **(char\*)**.</span><span class="sxs-lookup"><span data-stu-id="f432a-129">In a class by value **(char\*)**.</span></span>|<span data-ttu-id="f432a-130">Przekazuje ciągów w klasie (klasa jest parametrem We/Wy).</span><span class="sxs-lookup"><span data-stu-id="f432a-130">Passes strings in a class (a class is an In/Out parameter).</span></span> <span data-ttu-id="f432a-131">Funkcji niezarządzanej oczekuje wskaźnika do buforu znaków.</span><span class="sxs-lookup"><span data-stu-id="f432a-131">The unmanaged function expects a pointer to a character buffer.</span></span>|[<span data-ttu-id="f432a-132">OpenFileDlg</span><span class="sxs-lookup"><span data-stu-id="f432a-132">OpenFileDlg</span></span>](http://msdn.microsoft.com/library/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|<span data-ttu-id="f432a-133">W klasie przez wartość **(char[])**.</span><span class="sxs-lookup"><span data-stu-id="f432a-133">In a class by value **(char[])**.</span></span>|<span data-ttu-id="f432a-134">Przekazuje ciągów w klasie (klasa jest parametrem We/Wy).</span><span class="sxs-lookup"><span data-stu-id="f432a-134">Passes strings in a class (a class is an In/Out parameter).</span></span> <span data-ttu-id="f432a-135">Funkcji niezarządzanej oczekuje bufor osadzonych znaków.</span><span class="sxs-lookup"><span data-stu-id="f432a-135">The unmanaged function expects an embedded character buffer.</span></span>|[<span data-ttu-id="f432a-136">OSInfo</span><span class="sxs-lookup"><span data-stu-id="f432a-136">OSInfo</span></span>](http://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455)|  
|<span data-ttu-id="f432a-137">Jako tablica ciągów przez wartość.</span><span class="sxs-lookup"><span data-stu-id="f432a-137">As an array of strings by value.</span></span>|<span data-ttu-id="f432a-138">Tworzy tablicę ciągów, która jest przekazywany przez wartość.</span><span class="sxs-lookup"><span data-stu-id="f432a-138">Creates an array of strings that is passed by value.</span></span>|[<span data-ttu-id="f432a-139">Tablice</span><span class="sxs-lookup"><span data-stu-id="f432a-139">Arrays</span></span>](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|<span data-ttu-id="f432a-140">Jako tablica struktury zawierające ciągi przez wartość.</span><span class="sxs-lookup"><span data-stu-id="f432a-140">As an array of structures that contain strings by value.</span></span>|<span data-ttu-id="f432a-141">Tworzy tablicę struktur, które zawierają ciągi i tablicy jest przekazywany przez wartość.</span><span class="sxs-lookup"><span data-stu-id="f432a-141">Creates an array of structures that contain strings and the array is passed by value.</span></span>|[<span data-ttu-id="f432a-142">Tablice</span><span class="sxs-lookup"><span data-stu-id="f432a-142">Arrays</span></span>](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a><span data-ttu-id="f432a-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f432a-143">See Also</span></span>  
 [<span data-ttu-id="f432a-144">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="f432a-144">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 [<span data-ttu-id="f432a-145">Typy danych wywołanie platformy</span><span class="sxs-lookup"><span data-stu-id="f432a-145">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="f432a-146">Marshaling klas, struktur i unii</span><span class="sxs-lookup"><span data-stu-id="f432a-146">Marshaling Classes, Structures, and Unions</span></span>](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)  
 [<span data-ttu-id="f432a-147">Organizowanie tablice typów</span><span class="sxs-lookup"><span data-stu-id="f432a-147">Marshaling Arrays of Types</span></span>](http://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)  
 [<span data-ttu-id="f432a-148">Dodatkowe przykłady Marshalingu</span><span class="sxs-lookup"><span data-stu-id="f432a-148">Miscellaneous Marshaling Samples</span></span>](http://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70)
