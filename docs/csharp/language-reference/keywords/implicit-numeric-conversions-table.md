---
title: Tabela niejawnych konwersji liczbowych (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 4bbc6086dc5fd3838ef9361762c3068ca44efd0e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047984"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="25c07-102">Tabela niejawnych konwersji liczbowych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="25c07-102">Implicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="25c07-103">W poniższej tabeli przedstawiono wstępnie zdefiniowanych niejawnych konwersji liczbowych.</span><span class="sxs-lookup"><span data-stu-id="25c07-103">The following table shows the predefined implicit numeric conversions.</span></span> <span data-ttu-id="25c07-104">Niejawne konwersje mogą wystąpić w wielu sytuacjach, w tym metody wywoływania i przypisania poufności informacji.</span><span class="sxs-lookup"><span data-stu-id="25c07-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
|<span data-ttu-id="25c07-105">Z</span><span class="sxs-lookup"><span data-stu-id="25c07-105">From</span></span>|<span data-ttu-id="25c07-106">Zadanie</span><span class="sxs-lookup"><span data-stu-id="25c07-106">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="25c07-107">sbyte</span><span class="sxs-lookup"><span data-stu-id="25c07-107">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="25c07-108">`short`, `int`, `long`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="25c07-108">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="25c07-109">byte</span><span class="sxs-lookup"><span data-stu-id="25c07-109">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="25c07-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="25c07-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="25c07-111">short</span><span class="sxs-lookup"><span data-stu-id="25c07-111">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="25c07-112">`int`, `long`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="25c07-112">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="25c07-113">ushort</span><span class="sxs-lookup"><span data-stu-id="25c07-113">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="25c07-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="25c07-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="25c07-115">int</span><span class="sxs-lookup"><span data-stu-id="25c07-115">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="25c07-116">`long`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="25c07-116">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="25c07-117">uint</span><span class="sxs-lookup"><span data-stu-id="25c07-117">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="25c07-118">`long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="25c07-118">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="25c07-119">long</span><span class="sxs-lookup"><span data-stu-id="25c07-119">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="25c07-120">`float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="25c07-120">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="25c07-121">char</span><span class="sxs-lookup"><span data-stu-id="25c07-121">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="25c07-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="25c07-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="25c07-123">float</span><span class="sxs-lookup"><span data-stu-id="25c07-123">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[<span data-ttu-id="25c07-124">ulong</span><span class="sxs-lookup"><span data-stu-id="25c07-124">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="25c07-125">`float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="25c07-125">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25c07-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25c07-126">Remarks</span></span>  
  
-   <span data-ttu-id="25c07-127">Dokładności, ale wartość nie może być utracone w konwersje z `int`, `uint`, `long`, lub `ulong` do `float` i `long` lub `ulong` do `double`.</span><span class="sxs-lookup"><span data-stu-id="25c07-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`,  `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
-   <span data-ttu-id="25c07-128">Brak konwersji niejawnych do `char` typu.</span><span class="sxs-lookup"><span data-stu-id="25c07-128">There are no implicit conversions to the `char` type.</span></span>  
  
-   <span data-ttu-id="25c07-129">Brak niejawnej konwersji między typami zmiennoprzecinkowymi a `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="25c07-129">There are no implicit conversions between floating-point types and the `decimal` type.</span></span>  
  
-   <span data-ttu-id="25c07-130">Wyrażenie stałe typu `int` mogą być konwertowane na `sbyte`, `byte`, `short`, `ushort`, `uint`, lub `ulong`, o ile wartości stałe wyrażenia znajduje się w zakresie miejsca docelowego Typ.</span><span class="sxs-lookup"><span data-stu-id="25c07-130">A constant expression of type `int` can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided the value of the constant expression is within the range of the destination type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="25c07-131">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="25c07-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="25c07-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25c07-132">See Also</span></span>  

- [<span data-ttu-id="25c07-133">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="25c07-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="25c07-134">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="25c07-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="25c07-135">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="25c07-135">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="25c07-136">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="25c07-136">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="25c07-137">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="25c07-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
- [<span data-ttu-id="25c07-138">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="25c07-138">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
