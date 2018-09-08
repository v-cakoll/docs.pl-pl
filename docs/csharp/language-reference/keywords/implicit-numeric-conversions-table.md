---
title: Tabela niejawnych konwersji liczbowych (odwołanie w C#)
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: e46816fc8f3a6ff71dcba3561098d3cfce1e1054
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213267"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="bacae-102">Tabela niejawnych konwersji liczbowych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="bacae-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="bacae-103">W poniższej tabeli przedstawiono wstępnie zdefiniowanych niejawne konwersje między typów liczbowych .NET.</span><span class="sxs-lookup"><span data-stu-id="bacae-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="bacae-104">Z</span><span class="sxs-lookup"><span data-stu-id="bacae-104">From</span></span>|<span data-ttu-id="bacae-105">Zadanie</span><span class="sxs-lookup"><span data-stu-id="bacae-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="bacae-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="bacae-106">sbyte</span></span>](sbyte.md)|<span data-ttu-id="bacae-107">`short`, `int`, `long`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="bacae-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="bacae-108">byte</span><span class="sxs-lookup"><span data-stu-id="bacae-108">byte</span></span>](byte.md)|<span data-ttu-id="bacae-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="bacae-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="bacae-110">short</span><span class="sxs-lookup"><span data-stu-id="bacae-110">short</span></span>](short.md)|<span data-ttu-id="bacae-111">`int`, `long`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="bacae-111">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="bacae-112">ushort</span><span class="sxs-lookup"><span data-stu-id="bacae-112">ushort</span></span>](ushort.md)|<span data-ttu-id="bacae-113">`int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="bacae-113">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="bacae-114">int</span><span class="sxs-lookup"><span data-stu-id="bacae-114">int</span></span>](int.md)|<span data-ttu-id="bacae-115">`long`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="bacae-115">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="bacae-116">uint</span><span class="sxs-lookup"><span data-stu-id="bacae-116">uint</span></span>](uint.md)|<span data-ttu-id="bacae-117">`long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="bacae-117">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="bacae-118">long</span><span class="sxs-lookup"><span data-stu-id="bacae-118">long</span></span>](long.md)|<span data-ttu-id="bacae-119">`float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="bacae-119">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="bacae-120">char</span><span class="sxs-lookup"><span data-stu-id="bacae-120">char</span></span>](char.md)|<span data-ttu-id="bacae-121">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="bacae-121">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="bacae-122">float</span><span class="sxs-lookup"><span data-stu-id="bacae-122">float</span></span>](float.md)|`double`|  
|[<span data-ttu-id="bacae-123">ulong</span><span class="sxs-lookup"><span data-stu-id="bacae-123">ulong</span></span>](ulong.md)|<span data-ttu-id="bacae-124">`float`, `double`, lub `decimal`</span><span class="sxs-lookup"><span data-stu-id="bacae-124">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bacae-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bacae-125">Remarks</span></span>  

- <span data-ttu-id="bacae-126">Wszelkie [typu całkowitego](integral-types-table.md) jest niejawnie konwertowany na dowolny [typu zmiennoprzecinkowego](floating-point-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="bacae-126">Any [integral type](integral-types-table.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="bacae-127">Dokładności, ale wartość nie może być utracone w konwersje z `int`, `uint`, `long`, lub `ulong` do `float` i `long` lub `ulong` do `double`.</span><span class="sxs-lookup"><span data-stu-id="bacae-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="bacae-128">Brak konwersji niejawnych do `char` typu.</span><span class="sxs-lookup"><span data-stu-id="bacae-128">There are no implicit conversions to the `char` type.</span></span>  
  
- <span data-ttu-id="bacae-129">Brak niejawnej konwersji między `float` i `double` typów i `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="bacae-129">There are no implicit conversions between the `float` and `double` types and the `decimal` type.</span></span>  
  
- <span data-ttu-id="bacae-130">Wartości stałe wyrażenia typu `int` (na przykład, wartość reprezentowany przez całkowite literał) mogą być konwertowane na `sbyte`, `byte`, `short`, `ushort`, `uint`, lub `ulong`, o ile ma on w zakresie typu miejsca docelowego:</span><span class="sxs-lookup"><span data-stu-id="bacae-130">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="bacae-131">Aby uzyskać więcej informacji dotyczących niejawnych konwersji, zobacz [niejawne konwersje](/dotnet/csharp/language-reference/language-specification/conversions#implicit-conversions) części [specyfikacji języka C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="bacae-131">For more information about implicit conversions, see the [Implicit conversions](/dotnet/csharp/language-reference/language-specification/conversions#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bacae-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bacae-132">See also</span></span>

- [<span data-ttu-id="bacae-133">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bacae-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bacae-134">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bacae-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bacae-135">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="bacae-135">Integral types table</span></span>](integral-types-table.md)
- [<span data-ttu-id="bacae-136">Tabela typów zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="bacae-136">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="bacae-137">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="bacae-137">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="bacae-138">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="bacae-138">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="bacae-139">Konwersje rzutowania i typ</span><span class="sxs-lookup"><span data-stu-id="bacae-139">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
