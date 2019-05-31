---
title: Tabela typów całkowitych - C# odwołania
ms.custom: seodec18
description: Omówienie wbudowanego języka C# typy całkowite
ms.date: 08/20/2018
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
ms.assetid: 62e86126-46ff-40b0-9028-e61d7558268c
ms.openlocfilehash: b4a3a46ba98c0c621b747284ce39e03d68a5b62d
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421734"
---
# <a name="integral-types-table-c-reference"></a><span data-ttu-id="07b85-103">Tabela typów całkowitych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="07b85-103">Integral types table (C# Reference)</span></span>

<span data-ttu-id="07b85-104">W poniższej tabeli przedstawiono rozmiary i zakresy typów całkowitych, które stanowią podzbiór typów prostych.</span><span class="sxs-lookup"><span data-stu-id="07b85-104">The following table shows the sizes and ranges of the integral types, which constitute a subset of simple types.</span></span>  
  
|<span data-ttu-id="07b85-105">Typ</span><span class="sxs-lookup"><span data-stu-id="07b85-105">Type</span></span>|<span data-ttu-id="07b85-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="07b85-106">Range</span></span>|<span data-ttu-id="07b85-107">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="07b85-107">Size</span></span>|  
|----------|-----------|----------|  
|[<span data-ttu-id="07b85-108">sbyte</span><span class="sxs-lookup"><span data-stu-id="07b85-108">sbyte</span></span>](sbyte.md)|<span data-ttu-id="07b85-109">-128 do 127 znaków.</span><span class="sxs-lookup"><span data-stu-id="07b85-109">-128 to 127</span></span>|<span data-ttu-id="07b85-110">8-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="07b85-110">Signed 8-bit integer</span></span>|  
|[<span data-ttu-id="07b85-111">byte</span><span class="sxs-lookup"><span data-stu-id="07b85-111">byte</span></span>](byte.md)|<span data-ttu-id="07b85-112">od 0 do 255</span><span class="sxs-lookup"><span data-stu-id="07b85-112">0 to 255</span></span>|<span data-ttu-id="07b85-113">Liczba całkowita bez znaku 8-bitowa</span><span class="sxs-lookup"><span data-stu-id="07b85-113">Unsigned 8-bit integer</span></span>|  
|[<span data-ttu-id="07b85-114">char</span><span class="sxs-lookup"><span data-stu-id="07b85-114">char</span></span>](char.md)|<span data-ttu-id="07b85-115">U + 0000 do U + ffff</span><span class="sxs-lookup"><span data-stu-id="07b85-115">U+0000 to U+ffff</span></span>|<span data-ttu-id="07b85-116">Znak 16-bitowych Unicode</span><span class="sxs-lookup"><span data-stu-id="07b85-116">Unicode 16-bit character</span></span>|  
|[<span data-ttu-id="07b85-117">short</span><span class="sxs-lookup"><span data-stu-id="07b85-117">short</span></span>](short.md)|<span data-ttu-id="07b85-118">-32768 do 32767.</span><span class="sxs-lookup"><span data-stu-id="07b85-118">-32,768 to 32,767</span></span>|<span data-ttu-id="07b85-119">16-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="07b85-119">Signed 16-bit integer</span></span>|  
|[<span data-ttu-id="07b85-120">ushort</span><span class="sxs-lookup"><span data-stu-id="07b85-120">ushort</span></span>](ushort.md)|<span data-ttu-id="07b85-121">0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="07b85-121">0 to 65,535</span></span>|<span data-ttu-id="07b85-122">Liczba całkowita bez znaku 16-bitowych</span><span class="sxs-lookup"><span data-stu-id="07b85-122">Unsigned 16-bit integer</span></span>|  
|[<span data-ttu-id="07b85-123">int</span><span class="sxs-lookup"><span data-stu-id="07b85-123">int</span></span>](int.md)|<span data-ttu-id="07b85-124">-2 147 483 2 147 483 648 do 647</span><span class="sxs-lookup"><span data-stu-id="07b85-124">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="07b85-125">32-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="07b85-125">Signed 32-bit integer</span></span>|  
|[<span data-ttu-id="07b85-126">uint</span><span class="sxs-lookup"><span data-stu-id="07b85-126">uint</span></span>](uint.md)|<span data-ttu-id="07b85-127">4 294 967 0 Aby 295</span><span class="sxs-lookup"><span data-stu-id="07b85-127">0 to 4,294,967,295</span></span>|<span data-ttu-id="07b85-128">Liczba całkowita bez znaku 32-bitowy</span><span class="sxs-lookup"><span data-stu-id="07b85-128">Unsigned 32-bit integer</span></span>|  
|[<span data-ttu-id="07b85-129">long</span><span class="sxs-lookup"><span data-stu-id="07b85-129">long</span></span>](long.md)|<span data-ttu-id="07b85-130">-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="07b85-130">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="07b85-131">64-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="07b85-131">Signed 64-bit integer</span></span>|  
|[<span data-ttu-id="07b85-132">ulong</span><span class="sxs-lookup"><span data-stu-id="07b85-132">ulong</span></span>](ulong.md)|<span data-ttu-id="07b85-133">0 — 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="07b85-133">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="07b85-134">Liczba całkowita bez znaku 64-bitowych</span><span class="sxs-lookup"><span data-stu-id="07b85-134">Unsigned 64-bit integer</span></span>|  

## <a name="remarks"></a><span data-ttu-id="07b85-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07b85-135">Remarks</span></span>
  
<span data-ttu-id="07b85-136">Jeśli wartości w postaci literału typu integer przekracza <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, błąd kompilatora [CS1021](../../misc/cs1021.md) występuje.</span><span class="sxs-lookup"><span data-stu-id="07b85-136">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="07b85-137">Użyj <xref:System.Numerics.BigInteger?displayProperty=nameWithType> struktury do reprezentowania dowolnie dużą całkowita.</span><span class="sxs-lookup"><span data-stu-id="07b85-137">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent an arbitrarily large signed integer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="07b85-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07b85-138">See also</span></span>

- [<span data-ttu-id="07b85-139">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="07b85-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="07b85-140">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="07b85-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="07b85-141">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="07b85-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="07b85-142">Tabela typów zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="07b85-142">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="07b85-143">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="07b85-143">Default values table</span></span>](default-values-table.md)
- [<span data-ttu-id="07b85-144">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="07b85-144">Formatting numeric results table</span></span>](formatting-numeric-results-table.md)
- [<span data-ttu-id="07b85-145">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="07b85-145">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="07b85-146">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="07b85-146">Numerics in .NET</span></span>](../../../standard/numerics.md)
