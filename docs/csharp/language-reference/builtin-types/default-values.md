---
title: Domyślne wartości typów C# — odwołanie do języka C#
description: Poznaj domyślne wartości typów Języka C#, takich jak bool, char, int, float, double i inne.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 93b6079b9a3bbf6d537094cab9dfb305ace7f6bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625868"
---
# <a name="default-values-of-c-types-c-reference"></a><span data-ttu-id="25e72-103">Domyślne wartości typów C# (odwołanie c#)</span><span class="sxs-lookup"><span data-stu-id="25e72-103">Default values of C# types (C# reference)</span></span>

<span data-ttu-id="25e72-104">W poniższej tabeli przedstawiono wartości domyślne typów języka C#:</span><span class="sxs-lookup"><span data-stu-id="25e72-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="25e72-105">Typ</span><span class="sxs-lookup"><span data-stu-id="25e72-105">Type</span></span>|<span data-ttu-id="25e72-106">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="25e72-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="25e72-107">Dowolny typ odwołania</span><span class="sxs-lookup"><span data-stu-id="25e72-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="25e72-108">Każdy [wbudowany integralny typ numeryczny](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="25e72-108">Any [built-in integral numeric type](integral-numeric-types.md)</span></span>|<span data-ttu-id="25e72-109">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="25e72-109">0 (zero)</span></span>|
|<span data-ttu-id="25e72-110">Dowolny [wbudowany typ numeryczny zmiennoprzecinkowych](floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="25e72-110">Any [built-in floating-point numeric type](floating-point-numeric-types.md)</span></span>|<span data-ttu-id="25e72-111">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="25e72-111">0 (zero)</span></span>|
|[<span data-ttu-id="25e72-112">bool</span><span class="sxs-lookup"><span data-stu-id="25e72-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="25e72-113">char</span><span class="sxs-lookup"><span data-stu-id="25e72-113">char</span></span>](char.md)|<span data-ttu-id="25e72-114">`'\0'`(U+0000)</span><span class="sxs-lookup"><span data-stu-id="25e72-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="25e72-115">Enum</span><span class="sxs-lookup"><span data-stu-id="25e72-115">enum</span></span>](enum.md)|<span data-ttu-id="25e72-116">Wartość tworzona przez `(E)0`wyrażenie `E` , gdzie jest identyfikator emancypacji.</span><span class="sxs-lookup"><span data-stu-id="25e72-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="25e72-117">Struct</span><span class="sxs-lookup"><span data-stu-id="25e72-117">struct</span></span>](struct.md)|<span data-ttu-id="25e72-118">Wartość tworzona przez ustawienie wszystkich pól typu wartości na ich wartości `null`domyślne i wszystkie pola typu odwołania do .</span><span class="sxs-lookup"><span data-stu-id="25e72-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="25e72-119">Każdy [typ wartości z wartością null](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="25e72-119">Any [nullable value type](nullable-value-types.md)</span></span>|<span data-ttu-id="25e72-120">Wystąpienie, dla <xref:System.Nullable%601.HasValue%2A> którego `false` właściwość <xref:System.Nullable%601.Value%2A> jest i właściwość jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="25e72-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="25e72-121">Ta wartość domyślna jest również znana jako wartość *null* typu wartości null.</span><span class="sxs-lookup"><span data-stu-id="25e72-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="25e72-122">Użyj [domyślnego operatora,](../operators/default.md) aby wygenerować domyślną wartość typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="25e72-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="25e72-123">Począwszy od języka C# 7.1, można użyć [ `default` literału](../operators/default.md#default-literal) do zainicjowania zmiennej z wartością domyślną jej typu:</span><span class="sxs-lookup"><span data-stu-id="25e72-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="25e72-124">Dla typu wartości niejawny konstruktor bezparametrów tworzy również domyślną wartość tego typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="25e72-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="25e72-125">W czasie wykonywania, jeśli <xref:System.Type?displayProperty=nameWithType> wystąpienie reprezentuje typ wartości, można użyć <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> metody do wywołania konstruktora bezparametrowego w celu uzyskania wartości domyślnej typu.</span><span class="sxs-lookup"><span data-stu-id="25e72-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="25e72-126">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="25e72-126">C# language specification</span></span>

<span data-ttu-id="25e72-127">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="25e72-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="25e72-128">Wartości domyślne</span><span class="sxs-lookup"><span data-stu-id="25e72-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="25e72-129">Konstruktory domyślne</span><span class="sxs-lookup"><span data-stu-id="25e72-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="25e72-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25e72-130">See also</span></span>

- [<span data-ttu-id="25e72-131">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="25e72-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="25e72-132">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="25e72-132">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
