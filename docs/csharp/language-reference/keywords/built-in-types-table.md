---
title: Built-in types table - C# Reference
ms.custom: seodec18
description: Keywords for built-in C# types
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 77a927a7735d565390c8a5560312ee36b9e48925
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428544"
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="623ee-103">Built-in types table (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="623ee-103">Built-in types table (C# Reference)</span></span>

<span data-ttu-id="623ee-104">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace:</span><span class="sxs-lookup"><span data-stu-id="623ee-104">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace:</span></span>

|<span data-ttu-id="623ee-105">C# type</span><span class="sxs-lookup"><span data-stu-id="623ee-105">C# type</span></span>|<span data-ttu-id="623ee-106">.NET type</span><span class="sxs-lookup"><span data-stu-id="623ee-106">.NET type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="623ee-107">bool</span><span class="sxs-lookup"><span data-stu-id="623ee-107">bool</span></span>](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[<span data-ttu-id="623ee-108">byte</span><span class="sxs-lookup"><span data-stu-id="623ee-108">byte</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[<span data-ttu-id="623ee-109">sbyte</span><span class="sxs-lookup"><span data-stu-id="623ee-109">sbyte</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[<span data-ttu-id="623ee-110">char</span><span class="sxs-lookup"><span data-stu-id="623ee-110">char</span></span>](../builtin-types/char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[<span data-ttu-id="623ee-111">decimal</span><span class="sxs-lookup"><span data-stu-id="623ee-111">decimal</span></span>](../builtin-types/floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[<span data-ttu-id="623ee-112">double</span><span class="sxs-lookup"><span data-stu-id="623ee-112">double</span></span>](../builtin-types/floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[<span data-ttu-id="623ee-113">float</span><span class="sxs-lookup"><span data-stu-id="623ee-113">float</span></span>](../builtin-types/floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[<span data-ttu-id="623ee-114">int</span><span class="sxs-lookup"><span data-stu-id="623ee-114">int</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[<span data-ttu-id="623ee-115">uint</span><span class="sxs-lookup"><span data-stu-id="623ee-115">uint</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[<span data-ttu-id="623ee-116">long</span><span class="sxs-lookup"><span data-stu-id="623ee-116">long</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[<span data-ttu-id="623ee-117">ulong</span><span class="sxs-lookup"><span data-stu-id="623ee-117">ulong</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[<span data-ttu-id="623ee-118">object</span><span class="sxs-lookup"><span data-stu-id="623ee-118">object</span></span>](../builtin-types/reference-types.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[<span data-ttu-id="623ee-119">short</span><span class="sxs-lookup"><span data-stu-id="623ee-119">short</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[<span data-ttu-id="623ee-120">ushort</span><span class="sxs-lookup"><span data-stu-id="623ee-120">ushort</span></span>](../builtin-types/integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[<span data-ttu-id="623ee-121">string</span><span class="sxs-lookup"><span data-stu-id="623ee-121">string</span></span>](../builtin-types/reference-types.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a><span data-ttu-id="623ee-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="623ee-122">Remarks</span></span>

<span data-ttu-id="623ee-123">All of the types in the table, except `object` and `string`, are referred to as simple types.</span><span class="sxs-lookup"><span data-stu-id="623ee-123">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>

<span data-ttu-id="623ee-124">The .NET types and their C# type keyword aliases are interchangeable.</span><span class="sxs-lookup"><span data-stu-id="623ee-124">The .NET types and their C# type keyword aliases are interchangeable.</span></span> <span data-ttu-id="623ee-125">For example, you can declare an integer variable by using either of the following declarations:</span><span class="sxs-lookup"><span data-stu-id="623ee-125">For example, you can declare an integer variable by using either of the following declarations:</span></span>

```csharp
int x = 123;
System.Int32 y = 123;
```

<span data-ttu-id="623ee-126">Use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to get the <xref:System.Type?displayProperty=nameWithType> instance that represents the specified type:</span><span class="sxs-lookup"><span data-stu-id="623ee-126">Use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to get the <xref:System.Type?displayProperty=nameWithType> instance that represents the specified type:</span></span>

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a><span data-ttu-id="623ee-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="623ee-127">See also</span></span>

- [<span data-ttu-id="623ee-128">C# Reference</span><span class="sxs-lookup"><span data-stu-id="623ee-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="623ee-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="623ee-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="623ee-130">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="623ee-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="623ee-131">Value types</span><span class="sxs-lookup"><span data-stu-id="623ee-131">Value types</span></span>](value-types.md)
- [<span data-ttu-id="623ee-132">Reference types</span><span class="sxs-lookup"><span data-stu-id="623ee-132">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="623ee-133">Default values table</span><span class="sxs-lookup"><span data-stu-id="623ee-133">Default values table</span></span>](default-values-table.md)
- [<span data-ttu-id="623ee-134">dynamic</span><span class="sxs-lookup"><span data-stu-id="623ee-134">dynamic</span></span>](../builtin-types/reference-types.md)
