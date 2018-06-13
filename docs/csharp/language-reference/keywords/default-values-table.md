---
title: Tabela wartości domyślnych (odwołanie w C#)
description: Dowiedz się, jakie są wartości domyślne typy wartości zwracanych przez domyślnych konstruktorów.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 634a55304534b4269487f29be1fbb4930f51d8ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218793"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="d7894-103">Tabela wartości domyślnych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d7894-103">Default values table (C# Reference)</span></span>

<span data-ttu-id="d7894-104">W poniższej tabeli przedstawiono wartości domyślne typy wartości zwracanych przez domyślnych konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="d7894-104">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="d7894-105">Konstruktory domyślne są wywoływane przy użyciu `new` operatora w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d7894-105">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="d7894-106">Powyższych instrukcji ma ten sam efekt co następująca instrukcja:</span><span class="sxs-lookup"><span data-stu-id="d7894-106">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="d7894-107">Należy pamiętać, że przy użyciu niezainicjowanych zmiennych w języku C# nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="d7894-107">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="d7894-108">Typ wartości</span><span class="sxs-lookup"><span data-stu-id="d7894-108">Value type</span></span>|<span data-ttu-id="d7894-109">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="d7894-109">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="d7894-110">bool</span><span class="sxs-lookup"><span data-stu-id="d7894-110">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="d7894-111">byte</span><span class="sxs-lookup"><span data-stu-id="d7894-111">byte</span></span>](byte.md)|<span data-ttu-id="d7894-112">0</span><span class="sxs-lookup"><span data-stu-id="d7894-112">0</span></span>|
|[<span data-ttu-id="d7894-113">char</span><span class="sxs-lookup"><span data-stu-id="d7894-113">char</span></span>](char.md)|<span data-ttu-id="d7894-114">'\0'</span><span class="sxs-lookup"><span data-stu-id="d7894-114">'\0'</span></span>|
|[<span data-ttu-id="d7894-115">decimal</span><span class="sxs-lookup"><span data-stu-id="d7894-115">decimal</span></span>](decimal.md)|<span data-ttu-id="d7894-116">0M</span><span class="sxs-lookup"><span data-stu-id="d7894-116">0M</span></span>|
|[<span data-ttu-id="d7894-117">double</span><span class="sxs-lookup"><span data-stu-id="d7894-117">double</span></span>](double.md)|<span data-ttu-id="d7894-118">0,0 D</span><span class="sxs-lookup"><span data-stu-id="d7894-118">0.0D</span></span>|
|[<span data-ttu-id="d7894-119">enum</span><span class="sxs-lookup"><span data-stu-id="d7894-119">enum</span></span>](enum.md)|<span data-ttu-id="d7894-120">Wartość utworzonego przez wyrażenie (E) 0, gdzie E to identyfikator wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d7894-120">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="d7894-121">float</span><span class="sxs-lookup"><span data-stu-id="d7894-121">float</span></span>](float.md)|<span data-ttu-id="d7894-122">0,0</span><span class="sxs-lookup"><span data-stu-id="d7894-122">0.0F</span></span>|
|[<span data-ttu-id="d7894-123">int</span><span class="sxs-lookup"><span data-stu-id="d7894-123">int</span></span>](int.md)|<span data-ttu-id="d7894-124">0</span><span class="sxs-lookup"><span data-stu-id="d7894-124">0</span></span>|
|[<span data-ttu-id="d7894-125">long</span><span class="sxs-lookup"><span data-stu-id="d7894-125">long</span></span>](long.md)|<span data-ttu-id="d7894-126">0L</span><span class="sxs-lookup"><span data-stu-id="d7894-126">0L</span></span>|
|[<span data-ttu-id="d7894-127">sbyte</span><span class="sxs-lookup"><span data-stu-id="d7894-127">sbyte</span></span>](sbyte.md)|<span data-ttu-id="d7894-128">0</span><span class="sxs-lookup"><span data-stu-id="d7894-128">0</span></span>|
|[<span data-ttu-id="d7894-129">short</span><span class="sxs-lookup"><span data-stu-id="d7894-129">short</span></span>](short.md)|<span data-ttu-id="d7894-130">0</span><span class="sxs-lookup"><span data-stu-id="d7894-130">0</span></span>|
|[<span data-ttu-id="d7894-131">struct</span><span class="sxs-lookup"><span data-stu-id="d7894-131">struct</span></span>](struct.md)|<span data-ttu-id="d7894-132">Wartość utworzonego przez ustawienie wszystkie pola typu wartość do wartości domyślnych i wszystkie pola typu odwołania do `null`.</span><span class="sxs-lookup"><span data-stu-id="d7894-132">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="d7894-133">uint</span><span class="sxs-lookup"><span data-stu-id="d7894-133">uint</span></span>](uint.md)|<span data-ttu-id="d7894-134">0</span><span class="sxs-lookup"><span data-stu-id="d7894-134">0</span></span>|
|[<span data-ttu-id="d7894-135">ulong</span><span class="sxs-lookup"><span data-stu-id="d7894-135">ulong</span></span>](ulong.md)|<span data-ttu-id="d7894-136">0</span><span class="sxs-lookup"><span data-stu-id="d7894-136">0</span></span>|
|[<span data-ttu-id="d7894-137">ushort</span><span class="sxs-lookup"><span data-stu-id="d7894-137">ushort</span></span>](ushort.md)|<span data-ttu-id="d7894-138">0</span><span class="sxs-lookup"><span data-stu-id="d7894-138">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="d7894-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7894-139">See also</span></span>
 [<span data-ttu-id="d7894-140">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="d7894-140">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="d7894-141">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d7894-141">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="d7894-142">Tabela typów wartości</span><span class="sxs-lookup"><span data-stu-id="d7894-142">Value Types Table</span></span>](value-types-table.md)  
 [<span data-ttu-id="d7894-143">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="d7894-143">Value Types</span></span>](value-types.md)  
 [<span data-ttu-id="d7894-144">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="d7894-144">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="d7894-145">Tabele odwołań dla typów</span><span class="sxs-lookup"><span data-stu-id="d7894-145">Reference Tables for Types</span></span>](reference-tables-for-types.md)
