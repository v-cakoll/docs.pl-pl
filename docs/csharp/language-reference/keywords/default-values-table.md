---
title: Tabela wartości domyślnych (odwołanie w C#)
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
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
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e249dd2f352fe6177f3afbfd089fc4dc9b1b7798
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="d33df-102">Tabela wartości domyślnych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d33df-102">Default values table (C# Reference)</span></span>

<span data-ttu-id="d33df-103">W poniższej tabeli przedstawiono wartości domyślne typy wartości zwracanych przez domyślnych konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="d33df-103">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="d33df-104">Konstruktory domyślne są wywoływane przy użyciu `new` operatora w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d33df-104">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="d33df-105">Powyższych instrukcji ma ten sam efekt co następująca instrukcja:</span><span class="sxs-lookup"><span data-stu-id="d33df-105">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="d33df-106">Należy pamiętać, że przy użyciu niezainicjowanych zmiennych w języku C# nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="d33df-106">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="d33df-107">Typ wartości</span><span class="sxs-lookup"><span data-stu-id="d33df-107">Value type</span></span>|<span data-ttu-id="d33df-108">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="d33df-108">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="d33df-109">bool</span><span class="sxs-lookup"><span data-stu-id="d33df-109">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="d33df-110">byte</span><span class="sxs-lookup"><span data-stu-id="d33df-110">byte</span></span>](byte.md)|<span data-ttu-id="d33df-111">0</span><span class="sxs-lookup"><span data-stu-id="d33df-111">0</span></span>|
|[<span data-ttu-id="d33df-112">char</span><span class="sxs-lookup"><span data-stu-id="d33df-112">char</span></span>](char.md)|<span data-ttu-id="d33df-113">'\0'</span><span class="sxs-lookup"><span data-stu-id="d33df-113">'\0'</span></span>|
|[<span data-ttu-id="d33df-114">decimal</span><span class="sxs-lookup"><span data-stu-id="d33df-114">decimal</span></span>](decimal.md)|<span data-ttu-id="d33df-115">0M</span><span class="sxs-lookup"><span data-stu-id="d33df-115">0M</span></span>|
|[<span data-ttu-id="d33df-116">double</span><span class="sxs-lookup"><span data-stu-id="d33df-116">double</span></span>](double.md)|<span data-ttu-id="d33df-117">0,0 D</span><span class="sxs-lookup"><span data-stu-id="d33df-117">0.0D</span></span>|
|[<span data-ttu-id="d33df-118">enum</span><span class="sxs-lookup"><span data-stu-id="d33df-118">enum</span></span>](enum.md)|<span data-ttu-id="d33df-119">Wartość utworzonego przez wyrażenie (E) 0, gdzie E to identyfikator wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d33df-119">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="d33df-120">float</span><span class="sxs-lookup"><span data-stu-id="d33df-120">float</span></span>](float.md)|<span data-ttu-id="d33df-121">0,0</span><span class="sxs-lookup"><span data-stu-id="d33df-121">0.0F</span></span>|
|[<span data-ttu-id="d33df-122">int</span><span class="sxs-lookup"><span data-stu-id="d33df-122">int</span></span>](int.md)|<span data-ttu-id="d33df-123">0</span><span class="sxs-lookup"><span data-stu-id="d33df-123">0</span></span>|
|[<span data-ttu-id="d33df-124">long</span><span class="sxs-lookup"><span data-stu-id="d33df-124">long</span></span>](long.md)|<span data-ttu-id="d33df-125">0L</span><span class="sxs-lookup"><span data-stu-id="d33df-125">0L</span></span>|
|[<span data-ttu-id="d33df-126">sbyte</span><span class="sxs-lookup"><span data-stu-id="d33df-126">sbyte</span></span>](sbyte.md)|<span data-ttu-id="d33df-127">0</span><span class="sxs-lookup"><span data-stu-id="d33df-127">0</span></span>|
|[<span data-ttu-id="d33df-128">short</span><span class="sxs-lookup"><span data-stu-id="d33df-128">short</span></span>](short.md)|<span data-ttu-id="d33df-129">0</span><span class="sxs-lookup"><span data-stu-id="d33df-129">0</span></span>|
|[<span data-ttu-id="d33df-130">struct</span><span class="sxs-lookup"><span data-stu-id="d33df-130">struct</span></span>](struct.md)|<span data-ttu-id="d33df-131">Wartość utworzonego przez ustawienie wszystkie pola typu wartość do wartości domyślnych i wszystkie pola typu odwołania do `null`.</span><span class="sxs-lookup"><span data-stu-id="d33df-131">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="d33df-132">uint</span><span class="sxs-lookup"><span data-stu-id="d33df-132">uint</span></span>](uint.md)|<span data-ttu-id="d33df-133">0</span><span class="sxs-lookup"><span data-stu-id="d33df-133">0</span></span>|
|[<span data-ttu-id="d33df-134">ulong</span><span class="sxs-lookup"><span data-stu-id="d33df-134">ulong</span></span>](ulong.md)|<span data-ttu-id="d33df-135">0</span><span class="sxs-lookup"><span data-stu-id="d33df-135">0</span></span>|
|[<span data-ttu-id="d33df-136">ushort</span><span class="sxs-lookup"><span data-stu-id="d33df-136">ushort</span></span>](ushort.md)|<span data-ttu-id="d33df-137">0</span><span class="sxs-lookup"><span data-stu-id="d33df-137">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="d33df-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d33df-138">See also</span></span>
 [<span data-ttu-id="d33df-139">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="d33df-139">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="d33df-140">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d33df-140">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="d33df-141">Tabela typów wartości</span><span class="sxs-lookup"><span data-stu-id="d33df-141">Value Types Table</span></span>](value-types-table.md)  
 [<span data-ttu-id="d33df-142">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="d33df-142">Value Types</span></span>](value-types.md)  
 [<span data-ttu-id="d33df-143">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="d33df-143">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="d33df-144">Tabele odwołań dla typów</span><span class="sxs-lookup"><span data-stu-id="d33df-144">Reference Tables for Types</span></span>](reference-tables-for-types.md)
