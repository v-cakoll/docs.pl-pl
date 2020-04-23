---
title: x:Null — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: b83e893f951c15eca69fbb6b002369dd723ca469
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071431"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="56f57-102">x:Null — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="56f57-102">x:Null Markup Extension</span></span>

<span data-ttu-id="56f57-103">Określa `null` jako wartość dla elementu członkowskiego XAML.</span><span class="sxs-lookup"><span data-stu-id="56f57-103">Specifies `null` as a value for a XAML member.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="56f57-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="56f57-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a><span data-ttu-id="56f57-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56f57-105">Remarks</span></span>

<span data-ttu-id="56f57-106">Słowo kluczowe dla odwołania null w języku C# i C++ ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="56f57-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="56f57-107">Słowo kluczowe Microsoft Visual Basic `Nothing`dla odwołania null `{x:Null}` jest , ale zawsze używasz jako użycia XAML, niezależnie od tego, który język związany z kodem jest skojarzony z XAML.</span><span class="sxs-lookup"><span data-stu-id="56f57-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>

<span data-ttu-id="56f57-108">Rozszerzenie `x:Null` znaczników nie ma właściwości settable.</span><span class="sxs-lookup"><span data-stu-id="56f57-108">The `x:Null` markup extension has no settable properties.</span></span>

<span data-ttu-id="56f57-109">Użycie wartości null jest często skojarzone z ekspozycją <xref:System.Nullable%601> elementu członkowskiego XAML wartości CLR.</span><span class="sxs-lookup"><span data-stu-id="56f57-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>

<span data-ttu-id="56f57-110">Rozszerzenie `x:Null` znaczników, podobnie jak wszystkie rozszerzenia znaczników XAML,`{,}`używa nawiasów klamrowych ( ) do uciekania obsługi wartości atrybutów, które mają być inne niż literały lub odwołania do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="56f57-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="56f57-111">Składnia atrybutów jest składnią najczęściej używaną z tym rozszerzeniem znaczników.</span><span class="sxs-lookup"><span data-stu-id="56f57-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="56f57-112">Składnia elementu obiektu `<x:Null />` jest technicznie możliwa, ale `x:Null` jest rzadko używana, ponieważ rozszerzenie znaczników nie ma parametrów pozycyjnych ani argumentów konstrukcyjnych.</span><span class="sxs-lookup"><span data-stu-id="56f57-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>

<span data-ttu-id="56f57-113">Aby uzyskać informacje na temat rozszerzeń znaczników, zobacz [Rozszerzenia znaczników i WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="56f57-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>

<span data-ttu-id="56f57-114">W usługach .NET XAML obsługa tego rozszerzenia znaczników <xref:System.Windows.Markup.NullExtension> jest definiowana przez klasę.</span><span class="sxs-lookup"><span data-stu-id="56f57-114">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="56f57-115">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="56f57-115">WPF Usage Notes</span></span>

<span data-ttu-id="56f57-116">Należy `null` zauważyć, że niekoniecznie jest początkowa wartość unset dla właściwości zależności typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="56f57-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="56f57-117">Początkowa wartość domyślna może się różnić dla każdej właściwości zależności i może być oparta na metadanych specyficznych dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="56f57-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="56f57-118">Wiele właściwości zależności nie `null` akceptuje jako wartość, za pośrednictwem znaczników lub kodu ze względu na ich implementacje wywołania zwrotnego sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="56f57-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="56f57-119">Aby uzyskać więcej informacji na temat właściwości zależności, zobacz [Omówienie właściwości zależności](../../framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="56f57-119">For more information about dependency properties, see [Dependency Properties Overview](../../framework/wpf/advanced/dependency-properties-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="56f57-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56f57-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="56f57-121">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="56f57-121">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="56f57-122">Rozszerzenia znacznikowania i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="56f57-122">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
