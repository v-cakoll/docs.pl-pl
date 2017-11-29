---
title: "Tabela niejawnych konwersji liczbowych (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6b1705dca357fd2a155fc1ea9c7fe0f65bad8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="2886c-102">Tabela niejawnych konwersji liczbowych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="2886c-102">Implicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="2886c-103">W poniższej tabeli przedstawiono wstępnie zdefiniowane niejawne konwersje liczbowe.</span><span class="sxs-lookup"><span data-stu-id="2886c-103">The following table shows the predefined implicit numeric conversions.</span></span> <span data-ttu-id="2886c-104">Niejawne konwersje może wystąpić w wielu sytuacjach, w tym instrukcje metody wywoływania i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="2886c-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
|<span data-ttu-id="2886c-105">Z</span><span class="sxs-lookup"><span data-stu-id="2886c-105">From</span></span>|<span data-ttu-id="2886c-106">Do</span><span class="sxs-lookup"><span data-stu-id="2886c-106">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="2886c-107">sbyte —</span><span class="sxs-lookup"><span data-stu-id="2886c-107">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="2886c-108">`short`, `int`, `long`, `float`, `double`, lub`decimal`</span><span class="sxs-lookup"><span data-stu-id="2886c-108">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="2886c-109">bajtów</span><span class="sxs-lookup"><span data-stu-id="2886c-109">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="2886c-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub`decimal`</span><span class="sxs-lookup"><span data-stu-id="2886c-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="2886c-111">krótki</span><span class="sxs-lookup"><span data-stu-id="2886c-111">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="2886c-112">`int`, `long`, `float`, `double`, lub`decimal`</span><span class="sxs-lookup"><span data-stu-id="2886c-112">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="2886c-113">ushort</span><span class="sxs-lookup"><span data-stu-id="2886c-113">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="2886c-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, lub`decimal`</span><span class="sxs-lookup"><span data-stu-id="2886c-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="2886c-115">int</span><span class="sxs-lookup"><span data-stu-id="2886c-115">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="2886c-116">`long`, `float`, `double`, lub`decimal`</span><span class="sxs-lookup"><span data-stu-id="2886c-116">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="2886c-117">uint</span><span class="sxs-lookup"><span data-stu-id="2886c-117">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="2886c-118">`long`, `ulong`, `float`, `double`, lub`decimal`</span><span class="sxs-lookup"><span data-stu-id="2886c-118">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="2886c-119">długa</span><span class="sxs-lookup"><span data-stu-id="2886c-119">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="2886c-120">`float`, `double`, lub`decimal`</span><span class="sxs-lookup"><span data-stu-id="2886c-120">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="2886c-121">char</span><span class="sxs-lookup"><span data-stu-id="2886c-121">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="2886c-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub`decimal`</span><span class="sxs-lookup"><span data-stu-id="2886c-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="2886c-123">float</span><span class="sxs-lookup"><span data-stu-id="2886c-123">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[<span data-ttu-id="2886c-124">ulong</span><span class="sxs-lookup"><span data-stu-id="2886c-124">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="2886c-125">`float`, `double`, lub`decimal`</span><span class="sxs-lookup"><span data-stu-id="2886c-125">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2886c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2886c-126">Remarks</span></span>  
  
-   <span data-ttu-id="2886c-127">Dokładności, ale nie wielkości mogą zostać utracone podczas konwersji z `int`, `uint`, `long`, lub `ulong` do `float` i z `long` lub `ulong` do `double`.</span><span class="sxs-lookup"><span data-stu-id="2886c-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`,  `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
-   <span data-ttu-id="2886c-128">Brak niejawnej konwersji do `char` typu.</span><span class="sxs-lookup"><span data-stu-id="2886c-128">There are no implicit conversions to the `char` type.</span></span>  
  
-   <span data-ttu-id="2886c-129">Brak niejawnej konwersji między typami liczb zmiennoprzecinkowych i `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="2886c-129">There are no implicit conversions between floating-point types and the `decimal` type.</span></span>  
  
-   <span data-ttu-id="2886c-130">Wyrażenie stałe typu `int` może zostać przekonwertowany na `sbyte`, `byte`, `short`, `ushort`, `uint`, lub `ulong`, jeśli wartość wyrażenia stałej jest spoza zakresu docelowego Typ.</span><span class="sxs-lookup"><span data-stu-id="2886c-130">A constant expression of type `int` can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided the value of the constant expression is within the range of the destination type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="2886c-131">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2886c-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2886c-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2886c-132">See Also</span></span>  
 [<span data-ttu-id="2886c-133">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="2886c-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2886c-134">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2886c-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2886c-135">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="2886c-135">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="2886c-136">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="2886c-136">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="2886c-137">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="2886c-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="2886c-138">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="2886c-138">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
