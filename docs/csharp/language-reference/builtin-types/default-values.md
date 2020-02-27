---
title: Wartości domyślne C# typów — C# odwołanie
description: Poznaj wartości domyślne C# typów takich jak bool, char, int, float, Double i więcej.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 93b6079b9a3bbf6d537094cab9dfb305ace7f6bf
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625868"
---
# <a name="default-values-of-c-types-c-reference"></a><span data-ttu-id="9f848-103">Wartości domyślne C# typów (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="9f848-103">Default values of C# types (C# reference)</span></span>

<span data-ttu-id="9f848-104">W poniższej tabeli przedstawiono wartości domyślne C# typów:</span><span class="sxs-lookup"><span data-stu-id="9f848-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="9f848-105">Typ</span><span class="sxs-lookup"><span data-stu-id="9f848-105">Type</span></span>|<span data-ttu-id="9f848-106">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9f848-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="9f848-107">Dowolny typ referencyjny</span><span class="sxs-lookup"><span data-stu-id="9f848-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="9f848-108">Dowolny [wbudowany typ liczbowy całkowity](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="9f848-108">Any [built-in integral numeric type](integral-numeric-types.md)</span></span>|<span data-ttu-id="9f848-109">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="9f848-109">0 (zero)</span></span>|
|<span data-ttu-id="9f848-110">Dowolny [wbudowany typ liczbowy zmiennoprzecinkowy](floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="9f848-110">Any [built-in floating-point numeric type](floating-point-numeric-types.md)</span></span>|<span data-ttu-id="9f848-111">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="9f848-111">0 (zero)</span></span>|
|[<span data-ttu-id="9f848-112">bool</span><span class="sxs-lookup"><span data-stu-id="9f848-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="9f848-113">char</span><span class="sxs-lookup"><span data-stu-id="9f848-113">char</span></span>](char.md)|<span data-ttu-id="9f848-114">`'\0'` (U + 0000)</span><span class="sxs-lookup"><span data-stu-id="9f848-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="9f848-115">enum</span><span class="sxs-lookup"><span data-stu-id="9f848-115">enum</span></span>](enum.md)|<span data-ttu-id="9f848-116">Wartość wygenerowana przez wyrażenie `(E)0`, gdzie `E` jest identyfikatorem wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9f848-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="9f848-117">struct</span><span class="sxs-lookup"><span data-stu-id="9f848-117">struct</span></span>](struct.md)|<span data-ttu-id="9f848-118">Wartość wygenerowana przez ustawienie wszystkich pól typu wartość na wartości domyślne i wszystkie pola typu odwołania do `null`.</span><span class="sxs-lookup"><span data-stu-id="9f848-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="9f848-119">Dowolny [Typ wartości null](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="9f848-119">Any [nullable value type](nullable-value-types.md)</span></span>|<span data-ttu-id="9f848-120">Wystąpienie, dla którego właściwość <xref:System.Nullable%601.HasValue%2A> jest `false` i Właściwość <xref:System.Nullable%601.Value%2A> jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="9f848-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="9f848-121">Ta wartość domyślna jest również znana jako wartość *null* typu wartości null.</span><span class="sxs-lookup"><span data-stu-id="9f848-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="9f848-122">Użyj [operatora domyślnego](../operators/default.md) , aby utworzyć wartość domyślną typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9f848-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="9f848-123">Począwszy od C# 7,1, można użyć [literału`default`](../operators/default.md#default-literal) , aby zainicjować zmienną o wartości domyślnej typu:</span><span class="sxs-lookup"><span data-stu-id="9f848-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="9f848-124">Dla typu wartości niejawny Konstruktor bez parametrów tworzy również wartość domyślną typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9f848-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="9f848-125">W czasie wykonywania, jeśli wystąpienie <xref:System.Type?displayProperty=nameWithType> reprezentuje typ wartości, można użyć metody <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> do wywołania konstruktora bez parametrów, aby uzyskać wartość domyślną typu.</span><span class="sxs-lookup"><span data-stu-id="9f848-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9f848-126">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9f848-126">C# language specification</span></span>

<span data-ttu-id="9f848-127">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="9f848-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="9f848-128">Wartości domyślne</span><span class="sxs-lookup"><span data-stu-id="9f848-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="9f848-129">Konstruktory domyślne</span><span class="sxs-lookup"><span data-stu-id="9f848-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="9f848-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f848-130">See also</span></span>

- [<span data-ttu-id="9f848-131">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="9f848-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9f848-132">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="9f848-132">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
