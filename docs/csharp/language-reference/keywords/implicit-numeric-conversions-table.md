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
ms.openlocfilehash: f05ba1ee4e926f9f4c1b6427ecc60b41b45b06e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661454"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="7a208-102">Tabela niejawnych konwersji liczbowych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7a208-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="7a208-103">W poniższej tabeli przedstawiono wstępnie zdefiniowanych niejawne konwersje między typów liczbowych .NET.</span><span class="sxs-lookup"><span data-stu-id="7a208-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="7a208-104">Z</span><span class="sxs-lookup"><span data-stu-id="7a208-104">From</span></span>|<span data-ttu-id="7a208-105">Zadanie</span><span class="sxs-lookup"><span data-stu-id="7a208-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="7a208-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="7a208-106">sbyte</span></span>](sbyte.md)|<span data-ttu-id="7a208-107">`short`, `int`, `long`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="7a208-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7a208-108">byte</span><span class="sxs-lookup"><span data-stu-id="7a208-108">byte</span></span>](byte.md)|<span data-ttu-id="7a208-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="7a208-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7a208-110">char</span><span class="sxs-lookup"><span data-stu-id="7a208-110">char</span></span>](char.md)|<span data-ttu-id="7a208-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="7a208-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7a208-112">short</span><span class="sxs-lookup"><span data-stu-id="7a208-112">short</span></span>](short.md)|<span data-ttu-id="7a208-113">`int`, `long`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="7a208-113">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7a208-114">ushort</span><span class="sxs-lookup"><span data-stu-id="7a208-114">ushort</span></span>](ushort.md)|<span data-ttu-id="7a208-115">`int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="7a208-115">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7a208-116">int</span><span class="sxs-lookup"><span data-stu-id="7a208-116">int</span></span>](int.md)|<span data-ttu-id="7a208-117">`long`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="7a208-117">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7a208-118">uint</span><span class="sxs-lookup"><span data-stu-id="7a208-118">uint</span></span>](uint.md)|<span data-ttu-id="7a208-119">`long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="7a208-119">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7a208-120">long</span><span class="sxs-lookup"><span data-stu-id="7a208-120">long</span></span>](long.md)|<span data-ttu-id="7a208-121">`float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="7a208-121">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7a208-122">ulong</span><span class="sxs-lookup"><span data-stu-id="7a208-122">ulong</span></span>](ulong.md)|<span data-ttu-id="7a208-123">`float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="7a208-123">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="7a208-124">float</span><span class="sxs-lookup"><span data-stu-id="7a208-124">float</span></span>](float.md)|`double`|  
  
## <a name="remarks"></a><span data-ttu-id="7a208-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a208-125">Remarks</span></span>  

- <span data-ttu-id="7a208-126">Wszelkie [typu całkowitego](integral-types-table.md) jest niejawnie konwertowany na dowolny [typu zmiennoprzecinkowego](floating-point-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="7a208-126">Any [integral type](integral-types-table.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="7a208-127">Dokładności, ale wartość nie może być utracone w konwersje z `int`, `uint`, `long`, lub `ulong` do `float` i `long` lub `ulong` do `double`.</span><span class="sxs-lookup"><span data-stu-id="7a208-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="7a208-128">Brak konwersji niejawnych do `char`, `byte`, i `sbyte` typów.</span><span class="sxs-lookup"><span data-stu-id="7a208-128">There are no implicit conversions to the `char`, `byte`, and `sbyte` types.</span></span>  

- <span data-ttu-id="7a208-129">Brak niejawnej konwersji z `double` i `decimal` typów.</span><span class="sxs-lookup"><span data-stu-id="7a208-129">There are no implicit conversions from the `double` and `decimal` types.</span></span>
  
- <span data-ttu-id="7a208-130">Brak niejawnej konwersji między `decimal` typu i `float` lub `double` typów.</span><span class="sxs-lookup"><span data-stu-id="7a208-130">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>  
  
- <span data-ttu-id="7a208-131">Wartości stałe wyrażenia typu `int` (na przykład, wartość reprezentowany przez całkowite literał) mogą być konwertowane na `sbyte`, `byte`, `short`, `ushort`, `uint`, lub `ulong`, o ile ma on w zakresie typu miejsca docelowego:</span><span class="sxs-lookup"><span data-stu-id="7a208-131">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="7a208-132">Aby uzyskać więcej informacji dotyczących niejawnych konwersji, zobacz [niejawne konwersje](~/_csharplang/spec/conversions.md#implicit-conversions) części [specyfikacji języka C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="7a208-132">For more information about implicit conversions, see the [Implicit conversions](~/_csharplang/spec/conversions.md#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7a208-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a208-133">See also</span></span>

- [<span data-ttu-id="7a208-134">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7a208-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7a208-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7a208-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7a208-136">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="7a208-136">Integral types table</span></span>](integral-types-table.md)
- [<span data-ttu-id="7a208-137">Tabela typów zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="7a208-137">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="7a208-138">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="7a208-138">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="7a208-139">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="7a208-139">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="7a208-140">Konwersje rzutowania i typ</span><span class="sxs-lookup"><span data-stu-id="7a208-140">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
