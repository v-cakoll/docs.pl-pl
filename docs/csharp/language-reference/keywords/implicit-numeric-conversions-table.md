---
title: Tabela niejawnych konwersji liczbowych (odwołanie w C#)
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: c3c0153a0ae3e07839822c8bb978b1a09277bd53
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188706"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="4d91d-102">Tabela niejawnych konwersji liczbowych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4d91d-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="4d91d-103">W poniższej tabeli przedstawiono wstępnie zdefiniowanych niejawne konwersje między typów liczbowych .NET.</span><span class="sxs-lookup"><span data-stu-id="4d91d-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="4d91d-104">Z</span><span class="sxs-lookup"><span data-stu-id="4d91d-104">From</span></span>|<span data-ttu-id="4d91d-105">Zadanie</span><span class="sxs-lookup"><span data-stu-id="4d91d-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="4d91d-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="4d91d-106">sbyte</span></span>](sbyte.md)|<span data-ttu-id="4d91d-107">`short`, `int`, `long`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="4d91d-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4d91d-108">byte</span><span class="sxs-lookup"><span data-stu-id="4d91d-108">byte</span></span>](byte.md)|<span data-ttu-id="4d91d-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="4d91d-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4d91d-110">short</span><span class="sxs-lookup"><span data-stu-id="4d91d-110">short</span></span>](short.md)|<span data-ttu-id="4d91d-111">`int`, `long`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="4d91d-111">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4d91d-112">ushort</span><span class="sxs-lookup"><span data-stu-id="4d91d-112">ushort</span></span>](ushort.md)|<span data-ttu-id="4d91d-113">`int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="4d91d-113">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4d91d-114">int</span><span class="sxs-lookup"><span data-stu-id="4d91d-114">int</span></span>](int.md)|<span data-ttu-id="4d91d-115">`long`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="4d91d-115">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4d91d-116">uint</span><span class="sxs-lookup"><span data-stu-id="4d91d-116">uint</span></span>](uint.md)|<span data-ttu-id="4d91d-117">`long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="4d91d-117">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4d91d-118">long</span><span class="sxs-lookup"><span data-stu-id="4d91d-118">long</span></span>](long.md)|<span data-ttu-id="4d91d-119">`float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="4d91d-119">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4d91d-120">char</span><span class="sxs-lookup"><span data-stu-id="4d91d-120">char</span></span>](char.md)|<span data-ttu-id="4d91d-121">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="4d91d-121">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="4d91d-122">float</span><span class="sxs-lookup"><span data-stu-id="4d91d-122">float</span></span>](float.md)|`double`|  
|[<span data-ttu-id="4d91d-123">ulong</span><span class="sxs-lookup"><span data-stu-id="4d91d-123">ulong</span></span>](ulong.md)|<span data-ttu-id="4d91d-124">`float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="4d91d-124">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d91d-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d91d-125">Remarks</span></span>  

- <span data-ttu-id="4d91d-126">Wszelkie [typu całkowitego](integral-types-table.md) jest niejawnie konwertowany na dowolny [typu zmiennoprzecinkowego](floating-point-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="4d91d-126">Any [integral type](integral-types-table.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="4d91d-127">Dokładności, ale wartość nie może być utracone w konwersje z `int`, `uint`, `long`, lub `ulong` do `float` i `long` lub `ulong` do `double`.</span><span class="sxs-lookup"><span data-stu-id="4d91d-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="4d91d-128">Brak konwersji niejawnych do `char` typu.</span><span class="sxs-lookup"><span data-stu-id="4d91d-128">There are no implicit conversions to the `char` type.</span></span>  
  
- <span data-ttu-id="4d91d-129">Brak niejawnej konwersji między `float` i `double` typów i `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="4d91d-129">There are no implicit conversions between the `float` and `double` types and the `decimal` type.</span></span>  
  
- <span data-ttu-id="4d91d-130">Wartości stałe wyrażenia typu `int` (na przykład, wartość reprezentowany przez całkowite literał) mogą być konwertowane na `sbyte`, `byte`, `short`, `ushort`, `uint`, lub `ulong`, o ile ma on w zakresie typu miejsca docelowego:</span><span class="sxs-lookup"><span data-stu-id="4d91d-130">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="4d91d-131">Aby uzyskać więcej informacji dotyczących niejawnych konwersji, zobacz [niejawne konwersje](~/_csharplang/spec/conversions.md#implicit-conversions) części [specyfikacji języka C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4d91d-131">For more information about implicit conversions, see the [Implicit conversions](~/_csharplang/spec/conversions.md#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4d91d-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d91d-132">See also</span></span>

- [<span data-ttu-id="4d91d-133">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4d91d-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4d91d-134">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4d91d-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4d91d-135">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="4d91d-135">Integral types table</span></span>](integral-types-table.md)
- [<span data-ttu-id="4d91d-136">Tabela typów zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="4d91d-136">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="4d91d-137">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="4d91d-137">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="4d91d-138">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="4d91d-138">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="4d91d-139">Konwersje rzutowania i typ</span><span class="sxs-lookup"><span data-stu-id="4d91d-139">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
