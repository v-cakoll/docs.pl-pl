---
title: Tabela typów wbudowanych - C# odwołania
ms.custom: seodec18
description: Słowa kluczowe dla typy wbudowane C#
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: fae0cedfe8bf675dceb9cb9d5835d923cae8b4ab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662026"
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="86440-103">Tabela typów wbudowanych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="86440-103">Built-in types table (C# Reference)</span></span>

<span data-ttu-id="86440-104">W poniższej tabeli przedstawiono typy wbudowane C#, które są aliasy wstępnie zdefiniowanych typów słowa kluczowe w <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="86440-104">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace.</span></span>  
  
|<span data-ttu-id="86440-105">Typ C#</span><span class="sxs-lookup"><span data-stu-id="86440-105">C# type</span></span>|<span data-ttu-id="86440-106">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="86440-106">.NET type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="86440-107">bool</span><span class="sxs-lookup"><span data-stu-id="86440-107">bool</span></span>](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[<span data-ttu-id="86440-108">byte</span><span class="sxs-lookup"><span data-stu-id="86440-108">byte</span></span>](byte.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[<span data-ttu-id="86440-109">sbyte</span><span class="sxs-lookup"><span data-stu-id="86440-109">sbyte</span></span>](sbyte.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[<span data-ttu-id="86440-110">char</span><span class="sxs-lookup"><span data-stu-id="86440-110">char</span></span>](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[<span data-ttu-id="86440-111">decimal</span><span class="sxs-lookup"><span data-stu-id="86440-111">decimal</span></span>](decimal.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[<span data-ttu-id="86440-112">double</span><span class="sxs-lookup"><span data-stu-id="86440-112">double</span></span>](double.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[<span data-ttu-id="86440-113">float</span><span class="sxs-lookup"><span data-stu-id="86440-113">float</span></span>](float.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[<span data-ttu-id="86440-114">int</span><span class="sxs-lookup"><span data-stu-id="86440-114">int</span></span>](int.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[<span data-ttu-id="86440-115">uint</span><span class="sxs-lookup"><span data-stu-id="86440-115">uint</span></span>](uint.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[<span data-ttu-id="86440-116">long</span><span class="sxs-lookup"><span data-stu-id="86440-116">long</span></span>](long.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[<span data-ttu-id="86440-117">ulong</span><span class="sxs-lookup"><span data-stu-id="86440-117">ulong</span></span>](ulong.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[<span data-ttu-id="86440-118">object</span><span class="sxs-lookup"><span data-stu-id="86440-118">object</span></span>](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[<span data-ttu-id="86440-119">short</span><span class="sxs-lookup"><span data-stu-id="86440-119">short</span></span>](short.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[<span data-ttu-id="86440-120">ushort</span><span class="sxs-lookup"><span data-stu-id="86440-120">ushort</span></span>](ushort.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[<span data-ttu-id="86440-121">string</span><span class="sxs-lookup"><span data-stu-id="86440-121">string</span></span>](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a><span data-ttu-id="86440-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86440-122">Remarks</span></span>

<span data-ttu-id="86440-123">Wszystkie typy w tabeli, z wyjątkiem `object` i `string`, są nazywane typów prostych.</span><span class="sxs-lookup"><span data-stu-id="86440-123">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>  
  
<span data-ttu-id="86440-124">Słowa kluczowe typu C# i ich aliasy są wymienne.</span><span class="sxs-lookup"><span data-stu-id="86440-124">The C# type keywords and their aliases are interchangeable.</span></span> <span data-ttu-id="86440-125">Na przykład można zadeklarować zmienną całkowitoliczbową przy użyciu jednej z następujących deklaracje:</span><span class="sxs-lookup"><span data-stu-id="86440-125">For example, you can declare an integer variable by using either of the following declarations:</span></span>  

```csharp
int x = 123;
System.Int32 y = 123;
```

<span data-ttu-id="86440-126">Użyj [typeof](typeof.md) operatorem w celu uzyskania <xref:System.Type?displayProperty=nameWithType> wystąpienia, który reprezentuje określony typ:</span><span class="sxs-lookup"><span data-stu-id="86440-126">Use the [typeof](typeof.md) operator to get the <xref:System.Type?displayProperty=nameWithType> instance that represents the specified type:</span></span>

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a><span data-ttu-id="86440-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86440-127">See also</span></span>

- [<span data-ttu-id="86440-128">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="86440-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="86440-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="86440-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="86440-130">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="86440-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="86440-131">Tabele odwołań dla typów</span><span class="sxs-lookup"><span data-stu-id="86440-131">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="86440-132">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="86440-132">Value types</span></span>](value-types.md)
- [<span data-ttu-id="86440-133">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="86440-133">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="86440-134">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="86440-134">Default values table</span></span>](default-values-table.md)
- [<span data-ttu-id="86440-135">dynamic</span><span class="sxs-lookup"><span data-stu-id="86440-135">dynamic</span></span>](dynamic.md)
