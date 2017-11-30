---
title: "Tabela wartości domyślnych (odwołanie w C#)"
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.assetid: 4af2c1df-9e3a-48c1-83ac-b192986fc5bc
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d034c1daf495c50e299fec4c5bf399652dad08ce
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2017
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="273e7-102">Tabela wartości domyślnych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="273e7-102">Default values table (C# Reference)</span></span>
<span data-ttu-id="273e7-103">W poniższej tabeli przedstawiono wartości domyślne typy wartości zwracanych przez domyślnych konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="273e7-103">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="273e7-104">Konstruktory domyślne są wywoływane przy użyciu `new` operatora w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="273e7-104">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="273e7-105">Powyższych instrukcji ma ten sam efekt co następująca instrukcja:</span><span class="sxs-lookup"><span data-stu-id="273e7-105">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="273e7-106">Należy pamiętać, że przy użyciu niezainicjowanych zmiennych w języku C# nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="273e7-106">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="273e7-107">Typ wartości</span><span class="sxs-lookup"><span data-stu-id="273e7-107">Value type</span></span>|<span data-ttu-id="273e7-108">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="273e7-108">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="273e7-109">wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="273e7-109">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="273e7-110">bajtów</span><span class="sxs-lookup"><span data-stu-id="273e7-110">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="273e7-111">0</span><span class="sxs-lookup"><span data-stu-id="273e7-111">0</span></span>|
|[<span data-ttu-id="273e7-112">char</span><span class="sxs-lookup"><span data-stu-id="273e7-112">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="273e7-113">'\0'</span><span class="sxs-lookup"><span data-stu-id="273e7-113">'\0'</span></span>|
|[<span data-ttu-id="273e7-114">decimal</span><span class="sxs-lookup"><span data-stu-id="273e7-114">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|<span data-ttu-id="273e7-115">0M</span><span class="sxs-lookup"><span data-stu-id="273e7-115">0M</span></span>|
|[<span data-ttu-id="273e7-116">podwójne</span><span class="sxs-lookup"><span data-stu-id="273e7-116">double</span></span>](../../../csharp/language-reference/keywords/double.md)|<span data-ttu-id="273e7-117">0,0 D</span><span class="sxs-lookup"><span data-stu-id="273e7-117">0.0D</span></span>|
|[<span data-ttu-id="273e7-118">wyliczenia</span><span class="sxs-lookup"><span data-stu-id="273e7-118">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)|<span data-ttu-id="273e7-119">Wartość utworzonego przez wyrażenie (E) 0, gdzie E to identyfikator wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="273e7-119">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="273e7-120">float</span><span class="sxs-lookup"><span data-stu-id="273e7-120">float</span></span>](../../../csharp/language-reference/keywords/float.md)|<span data-ttu-id="273e7-121">0,0</span><span class="sxs-lookup"><span data-stu-id="273e7-121">0.0F</span></span>|
|[<span data-ttu-id="273e7-122">int</span><span class="sxs-lookup"><span data-stu-id="273e7-122">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="273e7-123">0</span><span class="sxs-lookup"><span data-stu-id="273e7-123">0</span></span>|
|[<span data-ttu-id="273e7-124">długa</span><span class="sxs-lookup"><span data-stu-id="273e7-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="273e7-125">0L</span><span class="sxs-lookup"><span data-stu-id="273e7-125">0L</span></span>|
|[<span data-ttu-id="273e7-126">sbyte —</span><span class="sxs-lookup"><span data-stu-id="273e7-126">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="273e7-127">0</span><span class="sxs-lookup"><span data-stu-id="273e7-127">0</span></span>|
|[<span data-ttu-id="273e7-128">krótki</span><span class="sxs-lookup"><span data-stu-id="273e7-128">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="273e7-129">0</span><span class="sxs-lookup"><span data-stu-id="273e7-129">0</span></span>|
|[<span data-ttu-id="273e7-130">— Struktura</span><span class="sxs-lookup"><span data-stu-id="273e7-130">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)|<span data-ttu-id="273e7-131">Wartość utworzonego przez ustawienie wszystkie pola typu wartość do wartości domyślnych i wszystkie pola typu odwołania do `null`.</span><span class="sxs-lookup"><span data-stu-id="273e7-131">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="273e7-132">uint</span><span class="sxs-lookup"><span data-stu-id="273e7-132">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="273e7-133">0</span><span class="sxs-lookup"><span data-stu-id="273e7-133">0</span></span>|
|[<span data-ttu-id="273e7-134">ulong</span><span class="sxs-lookup"><span data-stu-id="273e7-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="273e7-135">0</span><span class="sxs-lookup"><span data-stu-id="273e7-135">0</span></span>|
|[<span data-ttu-id="273e7-136">ushort</span><span class="sxs-lookup"><span data-stu-id="273e7-136">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="273e7-137">0</span><span class="sxs-lookup"><span data-stu-id="273e7-137">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="273e7-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="273e7-138">See also</span></span>
 [<span data-ttu-id="273e7-139">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="273e7-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="273e7-140">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="273e7-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="273e7-141">Tabela typów wartości</span><span class="sxs-lookup"><span data-stu-id="273e7-141">Value Types Table</span></span>](../../../csharp/language-reference/keywords/value-types-table.md)  
 [<span data-ttu-id="273e7-142">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="273e7-142">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="273e7-143">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="273e7-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="273e7-144">Tabele odwołań dla typów</span><span class="sxs-lookup"><span data-stu-id="273e7-144">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
