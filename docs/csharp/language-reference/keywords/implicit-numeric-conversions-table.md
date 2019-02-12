---
title: Tabela niejawnych konwersji liczbowych - C# odwołania
ms.custom: seodec18
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 703f60f48e1e569e0ffcab66ff7ccc91d4a49514
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093557"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="d9c04-102">Tabela niejawnych konwersji liczbowych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d9c04-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="d9c04-103">W poniższej tabeli przedstawiono wstępnie zdefiniowanych niejawne konwersje między typów liczbowych .NET.</span><span class="sxs-lookup"><span data-stu-id="d9c04-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="d9c04-104">Z</span><span class="sxs-lookup"><span data-stu-id="d9c04-104">From</span></span>|<span data-ttu-id="d9c04-105">Zadanie</span><span class="sxs-lookup"><span data-stu-id="d9c04-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="d9c04-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="d9c04-106">sbyte</span></span>](sbyte.md)|<span data-ttu-id="d9c04-107">`short`, `int`, `long`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="d9c04-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="d9c04-108">byte</span><span class="sxs-lookup"><span data-stu-id="d9c04-108">byte</span></span>](byte.md)|<span data-ttu-id="d9c04-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="d9c04-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="d9c04-110">char</span><span class="sxs-lookup"><span data-stu-id="d9c04-110">char</span></span>](char.md)|<span data-ttu-id="d9c04-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="d9c04-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="d9c04-112">short</span><span class="sxs-lookup"><span data-stu-id="d9c04-112">short</span></span>](short.md)|<span data-ttu-id="d9c04-113">`int`, `long`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="d9c04-113">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="d9c04-114">ushort</span><span class="sxs-lookup"><span data-stu-id="d9c04-114">ushort</span></span>](ushort.md)|<span data-ttu-id="d9c04-115">`int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="d9c04-115">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="d9c04-116">int</span><span class="sxs-lookup"><span data-stu-id="d9c04-116">int</span></span>](int.md)|<span data-ttu-id="d9c04-117">`long`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="d9c04-117">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="d9c04-118">uint</span><span class="sxs-lookup"><span data-stu-id="d9c04-118">uint</span></span>](uint.md)|<span data-ttu-id="d9c04-119">`long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="d9c04-119">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="d9c04-120">long</span><span class="sxs-lookup"><span data-stu-id="d9c04-120">long</span></span>](long.md)|<span data-ttu-id="d9c04-121">`float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="d9c04-121">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="d9c04-122">ulong</span><span class="sxs-lookup"><span data-stu-id="d9c04-122">ulong</span></span>](ulong.md)|<span data-ttu-id="d9c04-123">`float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="d9c04-123">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="d9c04-124">float</span><span class="sxs-lookup"><span data-stu-id="d9c04-124">float</span></span>](float.md)|`double`|  
  
## <a name="remarks"></a><span data-ttu-id="d9c04-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9c04-125">Remarks</span></span>  

- <span data-ttu-id="d9c04-126">Wszelkie [typu całkowitego](integral-types-table.md) jest niejawnie konwertowany na dowolny [typu zmiennoprzecinkowego](floating-point-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="d9c04-126">Any [integral type](integral-types-table.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="d9c04-127">Dokładności, ale wartość nie może być utracone w konwersje z `int`, `uint`, `long`, lub `ulong` do `float` i `long` lub `ulong` do `double`.</span><span class="sxs-lookup"><span data-stu-id="d9c04-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="d9c04-128">Brak konwersji niejawnych do `char`, `byte`, i `sbyte` typów.</span><span class="sxs-lookup"><span data-stu-id="d9c04-128">There are no implicit conversions to the `char`, `byte`, and `sbyte` types.</span></span>  

- <span data-ttu-id="d9c04-129">Brak niejawnej konwersji z `double` i `decimal` typów.</span><span class="sxs-lookup"><span data-stu-id="d9c04-129">There are no implicit conversions from the `double` and `decimal` types.</span></span>
  
- <span data-ttu-id="d9c04-130">Brak niejawnej konwersji między `decimal` typu i `float` lub `double` typów.</span><span class="sxs-lookup"><span data-stu-id="d9c04-130">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>  
  
- <span data-ttu-id="d9c04-131">Wartości stałe wyrażenia typu `int` (na przykład, wartość reprezentowany przez całkowite literał) mogą być konwertowane na `sbyte`, `byte`, `short`, `ushort`, `uint`, lub `ulong`, o ile ma on w zakresie typu miejsca docelowego:</span><span class="sxs-lookup"><span data-stu-id="d9c04-131">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="d9c04-132">Aby uzyskać więcej informacji dotyczących niejawnych konwersji, zobacz [niejawne konwersje](~/_csharplang/spec/conversions.md#implicit-conversions) części [specyfikacji języka C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d9c04-132">For more information about implicit conversions, see the [Implicit conversions](~/_csharplang/spec/conversions.md#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d9c04-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9c04-133">See also</span></span>

- [<span data-ttu-id="d9c04-134">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d9c04-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d9c04-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d9c04-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d9c04-136">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="d9c04-136">Integral types table</span></span>](integral-types-table.md)
- [<span data-ttu-id="d9c04-137">Tabela typów zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="d9c04-137">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="d9c04-138">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="d9c04-138">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="d9c04-139">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="d9c04-139">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="d9c04-140">Konwersje rzutowania i typ</span><span class="sxs-lookup"><span data-stu-id="d9c04-140">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
