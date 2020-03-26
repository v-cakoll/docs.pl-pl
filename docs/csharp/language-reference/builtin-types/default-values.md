---
title: Domyślne wartości typów C# — odwołanie do języka C#
description: Poznaj wartości domyślne typów języka C#, takich jak bool, char, int, float, double i inne.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 5e34d291ec15c738f3bc9409df321ede454b6710
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507259"
---
# <a name="default-values-of-c-types-c-reference"></a><span data-ttu-id="4325a-103">Domyślne wartości typów C# (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="4325a-103">Default values of C# types (C# reference)</span></span>

<span data-ttu-id="4325a-104">W poniższej tabeli przedstawiono wartości domyślne typów języka C#:</span><span class="sxs-lookup"><span data-stu-id="4325a-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="4325a-105">Typ</span><span class="sxs-lookup"><span data-stu-id="4325a-105">Type</span></span>|<span data-ttu-id="4325a-106">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4325a-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="4325a-107">Dowolny typ odwołania</span><span class="sxs-lookup"><span data-stu-id="4325a-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="4325a-108">Dowolny [wbudowany integralny typ numeryczny](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="4325a-108">Any [built-in integral numeric type](integral-numeric-types.md)</span></span>|<span data-ttu-id="4325a-109">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="4325a-109">0 (zero)</span></span>|
|<span data-ttu-id="4325a-110">Dowolny [wbudowany zmiennoprzecinowy typ numeryczny](floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="4325a-110">Any [built-in floating-point numeric type](floating-point-numeric-types.md)</span></span>|<span data-ttu-id="4325a-111">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="4325a-111">0 (zero)</span></span>|
|[<span data-ttu-id="4325a-112">bool</span><span class="sxs-lookup"><span data-stu-id="4325a-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="4325a-113">char</span><span class="sxs-lookup"><span data-stu-id="4325a-113">char</span></span>](char.md)|<span data-ttu-id="4325a-114">`'\0'`(U+0000)</span><span class="sxs-lookup"><span data-stu-id="4325a-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="4325a-115">Enum</span><span class="sxs-lookup"><span data-stu-id="4325a-115">enum</span></span>](enum.md)|<span data-ttu-id="4325a-116">Wartość wyprodukowana przez `(E)0`wyrażenie `E` , gdzie jest identyfikator wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4325a-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="4325a-117">Struct</span><span class="sxs-lookup"><span data-stu-id="4325a-117">struct</span></span>](struct.md)|<span data-ttu-id="4325a-118">Wartość powstała przez ustawienie wszystkich pól typu wartości na ich `null`wartości domyślne i wszystkie pola typu odwołania na .</span><span class="sxs-lookup"><span data-stu-id="4325a-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="4325a-119">Dowolny [typ wartości z do wartości możliwej do wartości null](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="4325a-119">Any [nullable value type](nullable-value-types.md)</span></span>|<span data-ttu-id="4325a-120">Wystąpienie, dla <xref:System.Nullable%601.HasValue%2A> którego `false` właściwość jest i <xref:System.Nullable%601.Value%2A> właściwość jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4325a-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="4325a-121">Ta wartość domyślna jest również znana jako wartość *null* typu wartości możliwej do wartości null.</span><span class="sxs-lookup"><span data-stu-id="4325a-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="4325a-122">Operator [ `default` służy](../operators/default.md#default-operator) do tworzenia wartości domyślnej typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4325a-122">Use the [`default` operator](../operators/default.md#default-operator) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="4325a-123">Począwszy od języka C# 7.1, można użyć [ `default` literału](../operators/default.md#default-literal) do zainicjowania zmiennej z domyślną wartością jej typu:</span><span class="sxs-lookup"><span data-stu-id="4325a-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="4325a-124">Dla typu wartości niejawny konstruktor bez parametrów również tworzy wartość domyślną typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4325a-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="4325a-125">W czasie wykonywania, <xref:System.Type?displayProperty=nameWithType> jeśli wystąpienie reprezentuje typ <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> wartości, można użyć metody do wywołania konstruktora bez parametrów, aby uzyskać domyślną wartość typu.</span><span class="sxs-lookup"><span data-stu-id="4325a-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4325a-126">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4325a-126">C# language specification</span></span>

<span data-ttu-id="4325a-127">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="4325a-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="4325a-128">Wartości domyślne</span><span class="sxs-lookup"><span data-stu-id="4325a-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="4325a-129">Konstruktory domyślne</span><span class="sxs-lookup"><span data-stu-id="4325a-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="4325a-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4325a-130">See also</span></span>

- [<span data-ttu-id="4325a-131">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4325a-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4325a-132">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="4325a-132">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
