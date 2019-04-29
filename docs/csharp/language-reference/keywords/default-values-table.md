---
title: Tabela wartości domyślnych - C# odwołania
ms.custom: seodec18
description: Dowiedz się, jakie są wartości domyślne w typach wartości języka C#.
ms.date: 08/23/2018
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- parameterless constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], parameterless constructor
- types [C#], parameterless constructor return values
ms.openlocfilehash: 1eb2fbc707b7c1ff9575e694457fa975f3d2e363
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661857"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="4ed53-103">Tabela wartości domyślnych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4ed53-103">Default values table (C# Reference)</span></span>

<span data-ttu-id="4ed53-104">W poniższej tabeli przedstawiono wartości domyślne [typy wartości](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="4ed53-104">The following table shows the default values of [value types](value-types.md).</span></span>

|<span data-ttu-id="4ed53-105">Typ wartości</span><span class="sxs-lookup"><span data-stu-id="4ed53-105">Value type</span></span>|<span data-ttu-id="4ed53-106">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4ed53-106">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="4ed53-107">bool</span><span class="sxs-lookup"><span data-stu-id="4ed53-107">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="4ed53-108">byte</span><span class="sxs-lookup"><span data-stu-id="4ed53-108">byte</span></span>](byte.md)|<span data-ttu-id="4ed53-109">0</span><span class="sxs-lookup"><span data-stu-id="4ed53-109">0</span></span>|
|[<span data-ttu-id="4ed53-110">char</span><span class="sxs-lookup"><span data-stu-id="4ed53-110">char</span></span>](char.md)|<span data-ttu-id="4ed53-111">'\0'</span><span class="sxs-lookup"><span data-stu-id="4ed53-111">'\0'</span></span>|
|[<span data-ttu-id="4ed53-112">decimal</span><span class="sxs-lookup"><span data-stu-id="4ed53-112">decimal</span></span>](decimal.md)|<span data-ttu-id="4ed53-113">0, M</span><span class="sxs-lookup"><span data-stu-id="4ed53-113">0M</span></span>|
|[<span data-ttu-id="4ed53-114">double</span><span class="sxs-lookup"><span data-stu-id="4ed53-114">double</span></span>](double.md)|<span data-ttu-id="4ed53-115">0.0 D</span><span class="sxs-lookup"><span data-stu-id="4ed53-115">0.0D</span></span>|
|[<span data-ttu-id="4ed53-116">enum</span><span class="sxs-lookup"><span data-stu-id="4ed53-116">enum</span></span>](enum.md)|<span data-ttu-id="4ed53-117">Wartość produkowane przez wyrażenie `(E)0`, gdzie `E` jest identyfikatorem wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4ed53-117">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="4ed53-118">float</span><span class="sxs-lookup"><span data-stu-id="4ed53-118">float</span></span>](float.md)|<span data-ttu-id="4ed53-119">0.0F</span><span class="sxs-lookup"><span data-stu-id="4ed53-119">0.0F</span></span>|
|[<span data-ttu-id="4ed53-120">int</span><span class="sxs-lookup"><span data-stu-id="4ed53-120">int</span></span>](int.md)|<span data-ttu-id="4ed53-121">0</span><span class="sxs-lookup"><span data-stu-id="4ed53-121">0</span></span>|
|[<span data-ttu-id="4ed53-122">long</span><span class="sxs-lookup"><span data-stu-id="4ed53-122">long</span></span>](long.md)|<span data-ttu-id="4ed53-123">0L</span><span class="sxs-lookup"><span data-stu-id="4ed53-123">0L</span></span>|
|[<span data-ttu-id="4ed53-124">sbyte</span><span class="sxs-lookup"><span data-stu-id="4ed53-124">sbyte</span></span>](sbyte.md)|<span data-ttu-id="4ed53-125">0</span><span class="sxs-lookup"><span data-stu-id="4ed53-125">0</span></span>|
|[<span data-ttu-id="4ed53-126">short</span><span class="sxs-lookup"><span data-stu-id="4ed53-126">short</span></span>](short.md)|<span data-ttu-id="4ed53-127">0</span><span class="sxs-lookup"><span data-stu-id="4ed53-127">0</span></span>|
|[<span data-ttu-id="4ed53-128">struct</span><span class="sxs-lookup"><span data-stu-id="4ed53-128">struct</span></span>](struct.md)|<span data-ttu-id="4ed53-129">Wartość produkowane przez ustawienie wszystkie pola typu wartości do wartości domyślnych i wszystkie pola typu odwołania do `null`.</span><span class="sxs-lookup"><span data-stu-id="4ed53-129">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="4ed53-130">uint</span><span class="sxs-lookup"><span data-stu-id="4ed53-130">uint</span></span>](uint.md)|<span data-ttu-id="4ed53-131">0</span><span class="sxs-lookup"><span data-stu-id="4ed53-131">0</span></span>|
|[<span data-ttu-id="4ed53-132">ulong</span><span class="sxs-lookup"><span data-stu-id="4ed53-132">ulong</span></span>](ulong.md)|<span data-ttu-id="4ed53-133">0</span><span class="sxs-lookup"><span data-stu-id="4ed53-133">0</span></span>|
|[<span data-ttu-id="4ed53-134">ushort</span><span class="sxs-lookup"><span data-stu-id="4ed53-134">ushort</span></span>](ushort.md)|<span data-ttu-id="4ed53-135">0</span><span class="sxs-lookup"><span data-stu-id="4ed53-135">0</span></span>|

## <a name="remarks"></a><span data-ttu-id="4ed53-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ed53-136">Remarks</span></span>

<span data-ttu-id="4ed53-137">Nie można użyć niezainicjowane zmienne w języku C#.</span><span class="sxs-lookup"><span data-stu-id="4ed53-137">You cannot use uninitialized variables in C#.</span></span> <span data-ttu-id="4ed53-138">Można zainicjować zmienną z wartością domyślną dla jego typu.</span><span class="sxs-lookup"><span data-stu-id="4ed53-138">You can initialize a variable with the default value of its type.</span></span> <span data-ttu-id="4ed53-139">Aby określić wartość domyślną metodę może zostać Użyj wartości domyślnej typu [opcjonalny argument](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments).</span><span class="sxs-lookup"><span data-stu-id="4ed53-139">You also can use the default value of a type to specify the default value of a method's [optional argument](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments).</span></span>

<span data-ttu-id="4ed53-140">Użyj [domyślne wyrażenie wartości](../../programming-guide/statements-expressions-operators/default-value-expressions.md) aby wygenerować wartość domyślna typu, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="4ed53-140">Use the [default value expression](../../programming-guide/statements-expressions-operators/default-value-expressions.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="4ed53-141">Począwszy od języka C# 7.1 można używać [ `default` literału](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) Aby zainicjalizować zmienną z wartością domyślną dla swojego typu:</span><span class="sxs-lookup"><span data-stu-id="4ed53-141">Beginning with C# 7.1, you can use the [`default` literal](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="4ed53-142">Możesz również umożliwia konstruktora bez parametrów lub niejawnego konstruktora bez parametrów generuje wartość domyślna typu wartości, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="4ed53-142">You also can use the parameterless constructor or the implicit parameterless constructor to produce the default value of a value type, as the following example shows.</span></span> <span data-ttu-id="4ed53-143">Aby uzyskać więcej informacji na temat konstruktorów, zobacz [konstruktory](../../programming-guide/classes-and-structs/constructors.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="4ed53-143">For more information about constructors, see the [Constructors](../../programming-guide/classes-and-structs/constructors.md) article.</span></span>

```csharp
int a = new int();
```

<span data-ttu-id="4ed53-144">Wartość domyślna dowolnej [odwołania do typu](reference-types.md) jest `null`.</span><span class="sxs-lookup"><span data-stu-id="4ed53-144">The default value of any [reference type](reference-types.md) is `null`.</span></span> <span data-ttu-id="4ed53-145">Wartość domyślna [typu dopuszczającego wartość null](../../programming-guide/nullable-types/index.md) jest wystąpieniem, dla którego <xref:System.Nullable%601.HasValue%2A> właściwość jest `false` i <xref:System.Nullable%601.Value%2A> właściwość jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4ed53-145">The default value of a [nullable type](../../programming-guide/nullable-types/index.md) is an instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ed53-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ed53-146">See also</span></span>

- [<span data-ttu-id="4ed53-147">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4ed53-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4ed53-148">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4ed53-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4ed53-149">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="4ed53-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4ed53-150">Tabele odwołań dla typów</span><span class="sxs-lookup"><span data-stu-id="4ed53-150">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="4ed53-151">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="4ed53-151">Value types</span></span>](value-types.md)
- [<span data-ttu-id="4ed53-152">Tabela typów wartości</span><span class="sxs-lookup"><span data-stu-id="4ed53-152">Value types table</span></span>](value-types-table.md)
- [<span data-ttu-id="4ed53-153">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="4ed53-153">Built-in types table</span></span>](built-in-types-table.md)
