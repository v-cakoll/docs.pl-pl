---
title: Tabela wartości domyślnych — C# odwołanie
ms.custom: seodec18
description: Dowiedz się, jakie są wartości C# domyślne typów.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 23fba8269670156000cb68b3aa07ae7c770eada1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627743"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="623e6-103">Tabela wartości domyślnych (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="623e6-103">Default values table (C# reference)</span></span>

<span data-ttu-id="623e6-104">W poniższej tabeli przedstawiono wartości domyślne C# typów:</span><span class="sxs-lookup"><span data-stu-id="623e6-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="623e6-105">Typ</span><span class="sxs-lookup"><span data-stu-id="623e6-105">Type</span></span>|<span data-ttu-id="623e6-106">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="623e6-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="623e6-107">Dowolny typ referencyjny</span><span class="sxs-lookup"><span data-stu-id="623e6-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="623e6-108">Dowolny [wbudowany typ liczbowy całkowity](../builtin-types/integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="623e6-108">Any [built-in integral numeric type](../builtin-types/integral-numeric-types.md)</span></span>|<span data-ttu-id="623e6-109">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="623e6-109">0 (zero)</span></span>|
|<span data-ttu-id="623e6-110">Dowolny [wbudowany typ liczbowy zmiennoprzecinkowy](../builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="623e6-110">Any [built-in floating-point numeric type](../builtin-types/floating-point-numeric-types.md)</span></span>|<span data-ttu-id="623e6-111">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="623e6-111">0 (zero)</span></span>|
|[<span data-ttu-id="623e6-112">bool</span><span class="sxs-lookup"><span data-stu-id="623e6-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="623e6-113">char</span><span class="sxs-lookup"><span data-stu-id="623e6-113">char</span></span>](char.md)|<span data-ttu-id="623e6-114">`'\0'`(U + 0000)</span><span class="sxs-lookup"><span data-stu-id="623e6-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="623e6-115">enum</span><span class="sxs-lookup"><span data-stu-id="623e6-115">enum</span></span>](enum.md)|<span data-ttu-id="623e6-116">Wartość wygenerowana przez wyrażenie `(E)0`, gdzie `E` jest identyfikatorem wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="623e6-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="623e6-117">struct</span><span class="sxs-lookup"><span data-stu-id="623e6-117">struct</span></span>](struct.md)|<span data-ttu-id="623e6-118">Wartość wygenerowana przez ustawienie wszystkich pól typu wartość na wartości domyślne i wszystkie pola typu odwołania do `null`.</span><span class="sxs-lookup"><span data-stu-id="623e6-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="623e6-119">Dowolny [Typ wartości null](../../programming-guide/nullable-types/index.md)</span><span class="sxs-lookup"><span data-stu-id="623e6-119">Any [nullable value type](../../programming-guide/nullable-types/index.md)</span></span>|<span data-ttu-id="623e6-120">Wystąpienie, dla którego <xref:System.Nullable%601.HasValue%2A> właściwość jest `false` i <xref:System.Nullable%601.Value%2A> właściwość jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="623e6-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="623e6-121">Ta wartość domyślna jest również znana jako wartość *null* typu wartości null.</span><span class="sxs-lookup"><span data-stu-id="623e6-121">That default value is also known as the *null* value of the nullable value type.</span></span>|

<span data-ttu-id="623e6-122">Użyj [wyrażenia wartości domyślnej](../../programming-guide/statements-expressions-operators/default-value-expressions.md) , aby utworzyć wartość domyślną typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="623e6-122">Use the [default value expression](../../programming-guide/statements-expressions-operators/default-value-expressions.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="623e6-123">Począwszy od C# 7,1, można użyć [ `default` literału](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) , aby zainicjować zmienną o wartości domyślnej typu:</span><span class="sxs-lookup"><span data-stu-id="623e6-123">Beginning with C# 7.1, you can use the [`default` literal](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="623e6-124">Dla typu wartości niejawny Konstruktor bez parametrów tworzy również wartość domyślną typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="623e6-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a><span data-ttu-id="623e6-125">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="623e6-125">C# language specification</span></span>

<span data-ttu-id="623e6-126">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="623e6-126">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="623e6-127">Wartości domyślne</span><span class="sxs-lookup"><span data-stu-id="623e6-127">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="623e6-128">Konstruktory domyślne</span><span class="sxs-lookup"><span data-stu-id="623e6-128">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="623e6-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="623e6-129">See also</span></span>

- [<span data-ttu-id="623e6-130">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="623e6-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="623e6-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="623e6-131">C# keywords</span></span>](index.md)
- [<span data-ttu-id="623e6-132">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="623e6-132">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="623e6-133">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="623e6-133">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
