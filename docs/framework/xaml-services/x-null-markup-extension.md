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
ms.openlocfilehash: ff82b0bfc1983240431e582dbd78778dc4469241
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459944"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="d9d1f-102">x:Null — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="d9d1f-102">x:Null Markup Extension</span></span>
<span data-ttu-id="d9d1f-103">Określa `null` jako wartość elementu członkowskiego języka XAML.</span><span class="sxs-lookup"><span data-stu-id="d9d1f-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="d9d1f-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="d9d1f-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="d9d1f-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9d1f-105">Remarks</span></span>  
 <span data-ttu-id="d9d1f-106">Słowo kluczowe dla odwołania o wartości null C# w C++ i ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="d9d1f-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="d9d1f-107">Słowo kluczowe Microsoft Visual Basic dla odwołania o wartości null jest `Nothing`, ale zawsze używasz `{x:Null}` jako użycia XAML niezależnie od tego, jaki język związany z kodem jest skojarzony z XAML.</span><span class="sxs-lookup"><span data-stu-id="d9d1f-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="d9d1f-108">Rozszerzenie znacznika `x:Null` nie ma właściwości settable.</span><span class="sxs-lookup"><span data-stu-id="d9d1f-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="d9d1f-109">Użycie wartości null jest często związane z narażeniem elementu członkowskiego języka XAML na wartość <xref:System.Nullable%601> CLR.</span><span class="sxs-lookup"><span data-stu-id="d9d1f-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="d9d1f-110">`x:Null` rozszerzenie znacznika, podobnie jak wszystkie rozszerzenia znaczników XAML, używa nawiasów (`{,}`) do ucieczki obsługi wartości atrybutów, aby były inne niż literały lub odwołania do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d9d1f-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="d9d1f-111">Składnia atrybutu jest składnią najczęściej używaną z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="d9d1f-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="d9d1f-112">Składnia elementu obiektu `<x:Null />` jest technicznie możliwa, ale rzadko jest używana, ponieważ rozszerzenie znaczników `x:Null` nie ma parametrów pozycyjnych ani argumentów konstrukcyjnych.</span><span class="sxs-lookup"><span data-stu-id="d9d1f-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="d9d1f-113">Aby uzyskać informacje na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników i XAML WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="d9d1f-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="d9d1f-114">W .NET Framework usługach XAML obsługa tego rozszerzenia znacznika jest definiowana przez klasę <xref:System.Windows.Markup.NullExtension>.</span><span class="sxs-lookup"><span data-stu-id="d9d1f-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="d9d1f-115">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="d9d1f-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="d9d1f-116">Należy pamiętać, że `null` nie musi być początkową wartością ustawienia dla właściwości zależności typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="d9d1f-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="d9d1f-117">Początkowa wartość domyślna może różnić się w zależności od właściwości zależności i może opierać się na metadanych specyficznych dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="d9d1f-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="d9d1f-118">Wiele właściwości zależności nie akceptuje `null` jako wartości, za pomocą znaczników ani kodu z powodu implementacji wywołania zwrotnego walidacji.</span><span class="sxs-lookup"><span data-stu-id="d9d1f-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="d9d1f-119">Aby uzyskać więcej informacji na temat właściwości zależności, zobacz [Omówienie właściwości zależności](../wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d9d1f-119">For more information about dependency properties, see [Dependency Properties Overview](../wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9d1f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9d1f-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="d9d1f-121">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="d9d1f-121">XAML Overview (WPF)</span></span>](../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="d9d1f-122">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="d9d1f-122">Markup Extensions and WPF XAML</span></span>](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
